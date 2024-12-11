<script setup>
defineProps(['todo'])
</script>

<template>
  <li>
    <input type="checkbox" :checked="todo.completed" @change="$emit('toggle-complete')" />
    <span :class="{ completed: todo.completed }">{{ todo.task }}</span>
    <button @click="$emit('delete-todo')">Delete</button>
  </li>
</template>

<style scoped>

.completed {
  text-decoration: line-through;
}
</style>
