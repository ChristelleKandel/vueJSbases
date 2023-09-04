<script setup>
import { ref } from 'vue'
const emit = defineEmits(['updateName'])
const handleUpdate = (event) => {
    emit('updateName', event.target.value)
}
const name = ref('')
</script>

<template>
  <div>
    <h1>Communication event parent enfant</h1>
    {{ name }}
    <input type="text" v-model="name" @input="handleUpdate">
    
  </div>
</template>

<style scoped>
</style>