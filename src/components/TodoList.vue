<script setup>
import TodoListItem from './TodoListItem.vue';

const response = await fetch('https://jsonplaceholder.typicode.com/todos');
const todos = await response.json();
const nameVar = "def";
</script>

<template>
    <ul>
        <TodoListItem
            v-for="todo of todos"
            :key="todo.id"
            :id="todo.id"
            :title="todo.title"
            :completed="todo.completed"
        />
    </ul>
</template>

<style scoped>

</style>