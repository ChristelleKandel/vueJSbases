<script setup>
const props = defineProps([
  'bienvenue', 'subTitle', 'nom', 'age'
])
</script>

<template>
  <div>
    <h3>Bienvenue {{ subTitle }}</h3>
    <p>
      <!-- Je peux mettre indifferemment le nom de ma variable ou props.variable -->
      <!-- Si ma variable est un objet comme user, je dois spécifier quelle valeur de mon objet j'appelle objet.variable-->
      {{ bienvenue }} à {{ nom }} qui a {{ props.age }} ans
    </p>
    
  </div>
</template>

<style scoped>
</style>