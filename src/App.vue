<!-- src/App.vue -->
<template>
  <div class="min-h-screen bg-gray-100 p-8">
    <h1 class="text-3xl font-bold text-center text-blue-500 mb-6">Vue 3 To-Do List</h1>
    <TodoList />
  </div>
</template>

<script setup>
import TodoList from './components/TodoList.vue'
</script>
