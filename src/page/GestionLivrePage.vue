<template>
    <div class="contenu">
      <div>
        <Livres :livres="livres"/>
      </div>
    </div>
</template>

<script setup>
import {ref}from 'vue';
import Livres from'../composants/Livres.vue';

const livres = ref([
 {id:1, titre:"Le Petit Prince",auteur:"Antoine de Saint-Exupéry",statut:"Disponible"},
 {id:2, titre:"1984",auteur:"George Orwell",statut:"Emprunte"},
 {id:3, titre:"Dune",auteur:"Frank Herbert",statut:"Disponible"},
 {id:4, titre:"L'Etranger",auteur:"Albert Camus",statut:"Emprunte"},
 ])
</script>