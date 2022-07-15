<script setup>
import TodoListItem from './TodoListItem.vue';
import { ref, reactive, toRefs, watch } from 'vue';

const response = await fetch('https://jsonplaceholder.typicode.com/todos');
let todos = await response.json();
todos = todos.slice(0, 10);
const reactiveTodos = ref(todos);

const counter = reactive({
    deleted: 0,
    updated: 0
});
// const counter = ref(0);

function getUpdatedCounter() {
    return counter.updated;
}

watch(() => counter.updated, (newValue, oldValue) => {
    console.log(`Counter updated ${oldValue} -> ${newValue}`);
});

function handleTodoItemDeleted(todoItemId) {
    reactiveTodos.value = reactiveTodos.value.filter(item => item.id !== todoItemId);
    counter.deleted++;
}

function handleTodoItemCompleted(todoItemId, completed) {
    reactiveTodos.value = reactiveTodos.value.map(todo => {
        if (todo.id === todoItemId) {
            return {
                ...todo,
                completed: completed
            }
        } else {
            return todo;
        }
    });
    counter.updated++;
}

const checkbox = ref(true);

watch(checkbox, newValue => {
    console.log(`checkbox: ${newValue}`);
});
</script>

<template>
    <span>Two-way data binding (v-model):</span>
    <input type="checkbox" v-model="checkbox" />
    <p>Updated: {{ counter.updated }}</p>
    <p>Deleted: {{ counter.deleted }}</p>
    <div class="todo-list">
        <TodoListItem
            v-for="todo of reactiveTodos"
            :key="todo.id"
            :id="todo.id"
            :title="todo.title"
            :completed="todo.completed"
            @todo-item-deleted="handleTodoItemDeleted(todo.id)"
            @todo-item-completed="completed => handleTodoItemCompleted(todo.id, completed)"
        />
    </div>
</template>

<style scoped>
.todo-list {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}
</style>