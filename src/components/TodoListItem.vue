<script setup>
defineProps({
    id: Number,
    title: String,
    completed: Boolean
})
</script>

<template>
    <div class="grid-container">
        <input type="checkbox" :checked="completed" />
        <p>{{ title }}</p>
        <button>Delete</button>
    </div>
</template>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: 1fr 4fr 1fr;
  background-color: #2196F3;
  padding: 10px;
}
.grid-item {
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  font-size: 30px;
  text-align: center;
}
button{
    justify-self: stretch;
}
input{
    justify-self: stretch;
}
p{
    justify-self: stretch;
}
</style>
