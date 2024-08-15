<!-- src/components/TodoItem.vue -->
<template>
    <li class="flex justify-between items-center py-2 border-b">
      <span :class="{ 'line-through': todo.completed }">{{ todo.text }}</span>
      <div>
        <button @click="toggle" class="text-sm text-green-500 mr-2">
          {{ todo.completed ? 'Undo' : 'Complete' }}
        </button>
        <button @click="remove" class="text-sm text-red-500">Remove</button>
      </div>
    </li>
  </template>
  
  <script setup>
  const props = defineProps({
    todo: Object,
  })
  
  const emit = defineEmits(['toggle-todo', 'remove-todo'])
  
  const toggle = () => {
    emit('toggle-todo', props.todo.id)
  }
  
  const remove = () => {
    emit('remove-todo', props.todo.id)
  }
  </script>
  
  <style scoped>
  .line-through {
    text-decoration: line-through;
  }
  </style>
  