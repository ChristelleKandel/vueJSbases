<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  },
  msgbis: {
    type: String,
    required: true
  },
})
</script>

<template>
  <div>
    <h1>{{ msg }} et {{ msgbis }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener noreferrer">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener noreferrer">Vue 3</a>.
    </h3>
  </div>
</template>

<style scoped>
</style>
