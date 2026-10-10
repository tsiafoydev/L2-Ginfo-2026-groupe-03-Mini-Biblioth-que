<template>
    <div class="contenu">
      <div>
          <Carte_stat :livres="livres"/>
      </div>
      <div>
        <Barre />
      </div>
      <div>
        <Livres :livres="livres" @supprimer="supprimeLivre" @modifier="ouvrirModification" />
      </div>
    </div>
    <Modifier v-if="afficheModal" :livre="livreEnEdition" @enregistrer="modifieLivre" @fermer="fermerModal"/>
</template>

<script setup>
import {ref}from 'vue';
import Livres from'../composants/Livres.vue';
import Barre from'../composants/Barre_action.vue';
import Carte_stat from '../composants/Carte_stat.vue';
import Modifier from '../composants/Modifier.vue';

const livres = ref([
 {id:1, titre:"Le Petit Prince",auteur:"Antoine de Saint-Exupéry",statut:"Disponible"},
 {id:2, titre:"1984",auteur:"George Orwell",statut:"Emprunte"},
 {id:3, titre:"Dune",auteur:"Frank Herbert",statut:"Disponible"},
 {id:4, titre:"L'Etranger",auteur:"Albert Camus",statut:"Emprunte"},
 ])

const afficheModal = ref(false)
const livreEnEdition = ref(null)

// Ouvrir la modal de modification
function ouvrirModification(livre) {
  livreEnEdition.value = livre
  afficheModal.value = true
}

function modifieLivre(livreModifie) {
  livres.value = livres.value.map(livre => {
    if (livre.id === livreModifie.id) {
      return livreModifie
    }
    return livre
  })
  fermerModal()
}
// Fermer la modal de modification
function fermerModal() {
  afficheModal.value = false
  livreEnEdition.value = null
}

</script>