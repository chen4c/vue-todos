<script setup>
import TodoItem from '@/components/TodoItem.vue'
defineProps(['todos'])
</script>

<template>
  <ul>
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-complete="$emit('toggle-complete', todo.id)"
      @delete-todo="$emit('delete-todo', todo.id)"
    />
  </ul>
</template>

<style scoped>

</style>
