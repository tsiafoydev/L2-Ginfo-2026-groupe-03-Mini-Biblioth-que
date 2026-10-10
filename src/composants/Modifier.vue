<template>
  <div class="modal-overlay" @click.self="emit('fermer')">
    <div class="modal">
      <div class="modal-header">
        <h2>Modifier le livre</h2>
      </div>

      <form @submit.prevent="valider" class="formulaire">
        <div class="champ">
          <label>Titre</label>
          <input v-model="titre" placeholder="Titre du livre" required>
        </div>

        <div class="champ">
          <label>Auteur</label>
          <input v-model="auteur" placeholder="Nom de l'auteur" required>
        </div>

        <div class="champ">
          <label>Statut</label>
          <select v-model="statut">
            <option value="Disponible">Disponible</option>
            <option value="Emprunte">Emprunté</option>
          </select>
        </div>

        <div class="action">
          <button type="button" class="btn-annuler" @click="emit('fermer')">
            Annuler
          </button>
          <button type="submit" class="btn-valider">
            Enregistrer
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import Modifier from '../composants/Modifier.vue';

const emit = defineEmits(['enregistrer', 'fermer'])

const props = defineProps({
  livre: {
    type: Object,
    required: true
  }
})

// Formulaire
const titre = ref('')
const auteur = ref('')
const statut = ref('Disponible')

// Preremplir dès l'ouverture
watch(
  () => props.livre,
  (livre) => {
    if (livre) {
      titre.value = livre.titre
      auteur.value = livre.auteur
      statut.value = livre.statut
    }
  },
  { immediate: true }
)

// Enregistrer
function valider() {
  emit('enregistrer', {
    id: props.livre.id,
    titre: titre.value,
    auteur: auteur.value,
    statut: statut.value
  })
}

</script>