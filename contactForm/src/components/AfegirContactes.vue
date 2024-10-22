<template>
  <div>
    <form @submit.prevent="afegirContacte">
      <input v-model="nom" id="nom" placeholder="Nom" required />
      <input v-model="telefon" id="telefon" placeholder="Telèfon" required />
      <button type="submit">Afegir Contacte</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Variables reactivas para almacenar la información del contacto
const nom = ref('');
const telefon = ref('');
// Definición del evento para emitir al componente padre
const emetre = defineEmits(['afegir-contacte']);

// Función para añadir un contacto
const afegirContacte = () => {
  if (nom.value && telefon.value) {
    // Crea un nuevo objeto contacto
    const nouContacte = {
      nom: nom.value,
      numero: telefon.value,
    };
    
    emetre('afegir-contacte', nouContacte); // Emitir el nuevo contacto al padre
    nom.value = ''; // Reiniciar el campo de nombre
    telefon.value = ''; // Reiniciar el campo de teléfono
  }
};
</script>

<style scoped>

form {
    display: flex; 
    flex-direction: column; 
    margin-bottom: 20px; 
}
</style>
