<template>
  <div class="conteneur">
    <h1>Ajouter un livre</h1>

    <form @submit.prevent="ajouteLivre" class="formulaire">
      <div class="champ">
        <label>Titre</label>
        <input v-model="titre" placeholder="Titre du livre">
      </div>

      <div class="champ">
        <label>Auteur</label>
        <input v-model="auteur" placeholder="Nom de l'auteur">
      </div>

      <div class="champ">
        <label>Statut</label>
        <select v-model="statut">
          <option value="Disponible">Disponible</option>
          <option value="Emprunte">Emprunté</option>
        </select>
      </div>

      <div class="action">
        <button type="submit">Ajouter</button>
        <button type="button" v-on:click="emit('fermer')">Annuler</button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['ajouter', 'fermer'])

const titre  = ref('')
const auteur = ref('')
const statut = ref('Disponible')

function ajouteLivre() {
  emit('ajouter', {
    titre:  titre.value,
    auteur: auteur.value,
    statut: statut.value,
  })

  titre.value  = ''
  auteur.value = ''
  statut.value = 'Disponible'
}

</script>

<style scoped>
.conteneur {
  background: #f9fafb;
  border: 1px solid #d6d7e9;
  border-radius: 12px;
  padding: 1.5rem;
  margin-top: 1.5rem;
  transition: .5s;
}

.conteneur h1 {
  font-size: 1.1rem;
  font-weight: 600;
  color: #333;
  margin-bottom: 1.25rem;
}

.formulaire {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.champ {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.champ label {
  font-size: 0.8rem;
  font-weight: 500;
  color: #555;
}

.champ input,
.champ select {
  padding: 0.6rem 0.85rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 0.9rem;
  font-family: inherit;
  background: #fff;
  outline: none;
  transition: border-color 0.2s, box-shadow 0.2s;
}

.champ input::placeholder {
  color: #aaa;
}

.champ input:focus,
.champ select:focus {
  border-color: #4f46e5;
  box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.1);
}

.action {
  display: flex;
  gap: 0.5rem;
  margin-top: 0.5rem;
}

.action button {
  padding: 0.6rem 1.2rem;
  border-radius: 8px;
  border: none;
  font-size: 0.9rem;
  font-weight: 500;
  font-family: inherit;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
}

.action button:active {
  transform: scale(0.98);
}

.action button[type="submit"] {
  background: #4f46e5;
  color: #fff;
}

.action button[type="submit"]:hover {
  background: #4338ca;
}

/* Bouton "Annuler" */
.action button[type="button"] {
  background: #fff;
  border: 1px solid #ddd;
  color: #333;
}

.action button[type="button"]:hover {
  background: #f3f4f6;
}
</style>