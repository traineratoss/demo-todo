<script setup>
defineProps({
    id: Number,
    title: String,
    completed: Boolean
})
</script>

<template>
    <input type="checkbox" :checked="completed" />
    <p>{{ title }}</p>
    <button>Delete</button>
</template>

<style scoped>
</style>