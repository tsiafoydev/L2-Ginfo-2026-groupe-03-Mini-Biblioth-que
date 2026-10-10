<template>
  <div class="barre_action">
    <button v-on:click="emit('toggle-form')">
      Ajoute
    </button>
    <input type="text" placeholder="Rechercher un livre..." v-model="recherche"/>
    <select v-model="statut">
      <option value="all">Tous les livres</option>
      <option value="disponible">Disponibles</option>
      <option value="emprunte">Empruntés</option>
    </select>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const recherche = defineModel('recherche', { type: String, default: '' })
const statut = defineModel('statut', { type: String, default: 'all' })

defineProps(['ouvert'])
const emit = defineEmits(['toggle-form'])

</script>

<style scoped>
.barre_action {
  display: flex;
  gap: 0.5rem;
  align-items: center;
  margin-bottom: 1.5rem;
}

.barre_action button {
  background: #4f46e5;
  color: #fff;
  border: none;
  padding: 0.6rem 1.2rem;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
  white-space: nowrap;
  font-family: inherit;
}

.barre_action button:hover {
  background: #4338ca;
}

.barre_action button:active {
  transform: scale(0.98);
}

.barre_action input {
  flex: 1;
  padding: 0.6rem 1rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 0.9rem;
  font-family: inherit;
  outline: none;
  transition: border 0.2s, box-shadow 0.2s;
  background: #fff;
}

.barre_action input::placeholder {
  color: #999;
}

.barre_action input:focus {
  border-color: #4f46e5;
  box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.1);
}

.barre_action select {
  padding: 0.6rem 1rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 0.9rem;
  font-family: inherit;
  background: #fff;
  color: #333;
  cursor: pointer;
  outline: none;
  transition: border 0.2s, box-shadow 0.2s;
}

.barre_action select:focus {
  border-color: #4f46e5;
  box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.1);
}
</style>