<template>
    <div>
      <h2>Llista de Contactes</h2>
      <ul>
        <li v-for="(contacte, index) in contactes" :key="index">
          {{ contacte.nom }} - 
          <a :href="'tel:' + contacte.numero">{{ contacte.numero }}</a> <!-- Enlace para realizar una llamada -->
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
      contactes: Array // Recibe la lista de contactos desde el componente padre
  });
  </script>
  
  <style scoped>


ul {
    list-style-type: none; 
    padding: 0; 
}

li {
    padding: 10px; 
}


  </style>
  