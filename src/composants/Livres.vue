<template>
    <h1>Liste des livre </h1>
    <div class="liste_livres">
      <p v-if="livres.length === 0" class="message_vide">
         Aucun livre trouvé
      </p>
        <div class="carte_livre" v-for="livre in livres" :key="livre.id">        
            <h1>{{ livre.titre }}</h1>
            <h3>{{ livre.auteur }}</h3>
            <span>{{ livre.statut }}</span>
            <div class="action">
                <button class="btn-mod">Modifier</button>
                <button class="btn-supp">Supprimer</button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

    defineProps({
        livres: { type: Array, required: true, default: () => [] }
    })


</script>

<style scoped>
.liste_livres {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 16px;
}

.message_vide {
  grid-column: 1 / -1;
  text-align: center;
  color: #6b7280;
  padding: 40px 20px;
  font-size: 1rem;
  background: #ffffff;
  border-radius: 12px;
  border: 2px dashed #e5e7eb;
}

.carte_livre {
  background: #ffffff;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  transition: transform 0.2s, box-shadow 0.2s, border-color 0.2s;
}

.carte_livre:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);
}

.carte_livre h1 {
  margin: 0;
  font-size: 1.1rem;
  color: #111827;
}

.carte_livre h3 {
  margin: 0;
  font-size: 0.9rem;
  color: #6b7280;
  font-weight: 500;
}


.action {
  display: flex;
  gap: 6px;
  margin-top: 8px;
}

.action button {
  flex: 1;
  padding: 6px 10px;
  border: none;
  border-radius: 6px;
  font-size: 0.8rem;
  font-family: inherit;
  cursor: pointer;
  transition: opacity 0.2s;
}

.action button:hover {
  opacity: 0.85;
}

.btn-mod {
  background: #6789c4;
  color: #1b17da;
}

.btn-supp {
  background: #fee2e2;
  color: #991b1b;
}
</style>