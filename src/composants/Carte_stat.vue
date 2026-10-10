<template>
  <div class="carte_conteneur">
    <div class="carte_stat">
      <span class="stat_label">Total des livres</span>
      <span class="stat_valeur">{{ total }}</span>
    </div>
    <div class="carte_stat">
      <span class="stat_label">Disponibles</span>
      <span class="stat_valeur">{{ disponibles }}</span>
    </div>
    <div class="carte_stat">
      <span class="stat_label"> Empruntés</span>
      <span class="stat_valeur">{{ empruntes }}</span>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

   const props = defineProps({
        livres: { type: Array, required: true, default: () => [] }
    })

    const total = computed(() => props.livres.length)

    const disponibles = computed(() =>
    props.livres.filter(l => l.statut === 'Disponible').length
    )

    const empruntes = computed(() =>
    props.livres.filter(l => l.statut === 'Emprunte').length
    )
</script>

<style scoped>
.carte_conteneur {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-bottom: 32px;
}

.carte_stat {
  background: #ffffff;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);
  border: 1px solid #e5e7eb;
  display: flex;
  flex-direction: column;
  gap: 8px;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.carte_stat:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
}

.stat_label {
  font-size: 0.9rem;
  color: #6b7280;
  font-weight: 500;
}

.stat_valeur {
  font-size: 1.8rem;
  font-weight: 700;
  color: #111827;
}

</style>