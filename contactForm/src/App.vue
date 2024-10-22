<template>
  <div id="app">
    <h1>Llibreta de Contactes</h1>
    <!-- Componente para agregar contactos -->
    <AfegirContactes @afegir-contacte="afegirContacte" />
    <!-- Campo de entrada para buscar contactos -->
    <input v-model="cercaContactes" placeholder="Introdueix el Nom del Contacte" class="input-nom" />
    <!-- Componente para mostrar la lista de contactos filtrados -->
    <BuscarContactes :contactes="filtrarContactes" />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import AfegirContactes from './components/AfegirContactes.vue';
import BuscarContactes from './components/BuscarContactes.vue';

// Lista de contactos reactiva
const contactes = ref([]);
// Campo de búsqueda reactivo
const cercaContactes = ref('');

// Computed para filtrar los contactos según el nombre
const filtrarContactes = computed(() => {
  if (!cercaContactes.value) {
    return contactes.value; // Si no hay búsqueda, devuelve todos los contactos
  }
  // Filtra los contactos que incluyen el texto de búsqueda
  return contactes.value.filter(contacte =>
    contacte.nom.toLowerCase().includes(cercaContactes.value.toLowerCase())
  );
});

// Función para añadir un nuevo contacto
const afegirContacte = (nouContacte) => {
  contactes.value.push(nouContacte); // Añade el nuevo contacto a la lista
};
</script>

<style scoped>

#app {
    max-width: 600px;
    margin: auto; 
    padding: 20px;
    background-color: #f78f8f;
    border-radius: 8px; 
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); 
}

h1 {
    text-align: center;
    color: #1E90FF; 
}


input[type="text"], input[type="tel"] {
    padding: 10px; 
    margin: 5px 0; 
    border: 1px solid #ccc; 
    border-radius: 4px; 
}

button {
    padding: 10px; 
    margin-top: 10px; 
    background-color: #1E90FF; 
    color: #ffffff; 
    border: none; 
    border-radius: 4px; 
    cursor: pointer; 
    transition: background-color 0.3s; 
}

button:hover {
    background-color: #0056b3; 
}

</style>
