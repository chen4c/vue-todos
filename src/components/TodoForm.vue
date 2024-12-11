<script setup lang="ts">
import {ref} from 'vue'
const task = ref<string>('')

const emit = defineEmits(['add-todo'])

function handleSubmit() {
  if (task.value.trim()) {
    emit('add-todo', task.value.trim())
    task.value = ''
  }
}
</script>

<template>
  <form @submit.prevent="handleSubmit">
    <input v-model="task" placeholder="Add task..." />
    <button type="submit">Add task</button>
  </form>
</template>

<style scoped>
</style>
