<!-- src/components/TodoList.vue -->
<template>
    <div class="max-w-xl mx-auto bg-white rounded-lg shadow-lg p-4">
      <AddTodo @add-todo="addTodo" />
      <ul>
        <TodoItem
          v-for="todo in todos"
          :key="todo.id"
          :todo="todo"
          @toggle-todo="toggleTodo"
          @remove-todo="removeTodo"
        />
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, watch } from 'vue'
  import AddTodo from './AddTodo.vue'
  import TodoItem from './TodoItem.vue'
  
  const todos = ref([])
  
  onMounted(() => {
    const savedTodos = JSON.parse(localStorage.getItem('todos')) || []
    todos.value = savedTodos
  })
  
  watch(todos, (newTodos) => {
    localStorage.setItem('todos', JSON.stringify(newTodos))
  }, { deep: true })
  
  const addTodo = (todoText) => {
    if (todoText.trim()) {
      todos.value.push({
        id: Date.now(),
        text: todoText,
        completed: false,
      })
    }
  }
  
  const toggleTodo = (id) => {
    const todo = todos.value.find(todo => todo.id === id)
    if (todo) {
      todo.completed = !todo.completed
    }
  }
  
  const removeTodo = (id) => {
    todos.value = todos.value.filter(todo => todo.id !== id)
  }
  </script>
  