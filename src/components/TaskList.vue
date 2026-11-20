<script setup>
import { ref, onMounted } from 'vue'
import TaskItem from './TaskItem.vue'

const tasks = ref([])
const loading = ref(true)
const error = ref(null)

onMounted(async () => {
  try {
    const response = await fetch(`${import.meta.env.VITE_BACKEND_URL}/tasks`)
    if (!response.ok) {
      throw new Error(`HTTP ${response.status}`)
    }
    tasks.value = await response.json()
  } catch (e) {
    error.value = 'Die Aufgaben konnten nicht geladen werden.'
  } finally {
    loading.value = false
  }
})
</script>

<template>
  <h2>Meine Aufgaben</h2>

  <p v-if="loading">Lade Aufgaben … (beim ersten Aufruf kann das bis zu einer Minute dauern)</p>
  <p v-else-if="error">{{ error }}</p>

  <ul v-else>
    <TaskItem v-for="task in tasks" :key="task.id" :task="task" />
  </ul>
</template>