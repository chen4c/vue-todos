<script setup>
import TodoList from '@/components/TodoList.vue'

import {ref} from 'vue'
import TodoForm from '@/components/TodoForm.vue'

const todos = ref([
  {
    id: 1,
    task: 'Learning Vue3',
    completed: true
  },
  {
    id: 2,
    task: 'Learning TypeScript',
    completed: false
  }
])

const addTodo = (task) => {
  todos.value.push({
    id: Date.now(),
    task,
    completed: false
  })
}

const toggleComplete = (id) => {
  const target = todos.value.find((todo) => todo.id === id)
  if (target) {
    target.completed = !target.completed
  }
}

const deleteTodo = (id) => {
  todos.value = todos.value.filter((todo) => todo.id !== id)
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  </header>

  <main>
    <h1>Todo List</h1>
    <TodoForm @addTodo="addTodo" />
    <TodoList
      :todos="todos"
      @toggle-complete="toggleComplete"
      @delete-todo="deleteTodo"
    />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
