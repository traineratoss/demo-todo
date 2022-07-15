<script setup>
import { computed, ref } from 'vue';
import printTodoItem from '../utils/printTodoItem';

const props = defineProps({
    id: Number,
    title: String,
    completed: Boolean
});

const emit = defineEmits(['todoItemDeleted', 'todoItemCompleted']);

const newTitle = computed(() => printTodoItem(props.id, props.title, props.completed));

function handleChange(event) {
    emit('todoItemCompleted', event.target.checked);
}
</script>

<template>
    <input type="checkbox" :checked="completed" @change="handleChange" />
    <p>{{ newTitle }}</p>
    <button @click="$emit('todoItemDeleted')">Delete</button>
</template>

<style scoped>
</style>