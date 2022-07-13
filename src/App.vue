<script setup>
import { RouterLink, RouterView } from 'vue-router';
</script>

<template>
    <header>
        <div>
            <nav>
                <RouterLink to="/" class="link">Home</RouterLink>
                <RouterLink to="/about" class="link">About</RouterLink>
            </nav>
        </div>
    </header>
    <RouterView />
</template>

<style scoped>
.link {
  margin-right: 10px;
}
</style>
