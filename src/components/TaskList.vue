<script setup>
import { ref } from 'vue'

const tasks = ref([
  { id: 1, title: 'Einkaufen', done: false },
  { id: 2, title: 'WebTech M1 abgeben', done: true },
  { id: 3, title: 'WebTech M2 abgeben', done: false }
])
</script>

<template>
  <h2>Meine Aufgaben</h2>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      {{ task.title }} – {{ task.done ? 'erledigt' : 'offen' }}
    </li>
  </ul>
</template>