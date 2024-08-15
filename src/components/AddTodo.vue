<!-- src/components/AddTodo.vue -->
<template>
    <form @submit.prevent="submitTodo" class="flex mb-4">
      <input
        v-model="newTodo"
        class="flex-grow px-4 py-2 border rounded-l-lg focus:outline-none"
        type="text"
        placeholder="Add a new task..."
      />
      <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded-r-lg">
        Add
      </button>
    </form>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const newTodo = ref('')
  
  const emit = defineEmits(['add-todo'])
  
  const submitTodo = () => {
    if (newTodo.value.trim()) {
      emit('add-todo', newTodo.value)
      newTodo.value = ''
    }
  }
  </script>
  