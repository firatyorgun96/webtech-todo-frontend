<script setup>
defineProps({
  task: Object
})
</script>

<template>
  <li>
    {{ task.title }} – {{ task.done ? 'erledigt' : 'offen' }}
  </li>
</template>