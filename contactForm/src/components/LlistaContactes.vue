<template>
    <div>
      <h2>Llista de Contactes</h2>
      <ul>
        <!-- Recorre la lista de contactes amb v-for -->
        <li v-for="(contacte, index) in contactes" :key="index">
          {{ contacte.nom }} - {{ contacte.numero }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>

const props = defineProps({
    contactes:Array
});

  </script>
  
  <style scoped>
 
  </style>
  