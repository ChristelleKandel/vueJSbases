<script setup>
</script>

<template>
  <div>
    <h3>Utilisateurs</h3>
    <!-- Je définie grâce au slot l'emplacement du contenu des variables déclarées chez le parent App.vue-->
    <slot name="name">
    </slot>
    <slot name="surname">
    </slot>
  </div>
</template>

<style scoped>
</style>