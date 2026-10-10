<script setup>
import Livres from '../composants/Livres.vue'
</script>

<template>
<main class="accueil">

  <!-- Section de bienvenue -->
  <section class="hero">
    <div class="hero-content">
      <span class="surtitre">VOTRE ESPACE DE LECTURE</span>

      <h1>
        Chaque livre ouvre<br />
        une nouvelle <span>histoire.</span>
      </h1>

      <p>
        Explorez notre bibliothèque, découvrez de nouveaux auteurs
        et trouvez votre prochaine lecture préférée.
      </p>

      <RouterLink to="/livres" class="bouton">
        Découvrir les livres
        <span>→</span>
      </RouterLink>
    </div>

    <div class="illustration">
      <div class="cercle"></div>
      <div class="livre livre-un">📘</div>
      <div class="livre livre-deux">📕</div>
      <div class="livre livre-trois">📗</div>
      <span class="etoile">✦</span>
    </div>
  </section>

  <!-- Présentation -->
  <section class="presentation">
    <span class="surtitre">UN MONDE À EXPLORER</span>
    <h2>Votre prochaine lecture vous attend.</h2>
    <p>
      Roman, aventure, développement personnel ou informatique :
      laissez-vous guider par votre curiosité.
    </p>
  </section>

  <!-- Réutilisation du composant existant -->
  <section class="decouvertes">
    <div class="section-entete">
      <div>
        <span class="surtitre">NOTRE COLLECTION</span>
        <h2>Des livres à découvrir</h2>
      </div>

      <RouterLink to="/livres" class="lien">
        Voir le catalogue →
      </RouterLink>
    </div>

    <Livres />
  </section>

</main>
</template>

<style scoped>
.accueil {
padding: 36px;
color: #172554;
background: #f8fafc;
min-height: 100vh;
}

.hero {
display: flex;
align-items: center;
justify-content: space-between;
gap: 30px;
padding: 48px;
border-radius: 24px;
background: #eef2ff;
overflow: hidden;
}

.hero-content {
flex: 1;
max-width: 540px;
}

.surtitre {
color: #4f46e5;
font-size: 12px;
font-weight: 700;
letter-spacing: 2px;
}

.hero h1 {
margin: 20px 0;
font-size: clamp(30px, 4vw, 48px);
line-height: 1.15;
}

.hero h1 span {
color: #4f46e5;
}

.hero p,
.presentation p {
color: #64748b;
line-height: 1.8;
}

.bouton {
display: inline-flex;
align-items: center;
gap: 18px;
margin-top: 18px;
padding: 14px 20px;
border-radius: 10px;
background: #4f46e5;
color: white;
text-decoration: none;
font-weight: 600;
transition: background 0.2s;
}

.bouton:hover {
background: #3730a3;
}

.illustration {
position: relative;
display: flex;
align-items: center;
justify-content: center;
flex: 0 0 280px;
height: 240px;
}

.cercle {
position: absolute;
width: 220px;
height: 220px;
border-radius: 50%;
background: #c7d2fe;
}

.livre {
position: relative;
display: grid;
place-items: center;
width: 75px;
height: 110px;
border-radius: 8px;
font-size: 48px;
box-shadow: 0 12px 20px #17255420;
}

.livre-un {
transform: rotate(-12deg) translateY(8px);
background: #dbeafe;
}

.livre-deux {
z-index: 1;
transform: translateY(-12px);
background: #fef3c7;
}

.livre-trois {
transform: rotate(12deg) translateY(8px);
background: #dcfce7;
}

.etoile {
position: absolute;
top: 15px;
right: 10px;
color: #4f46e5;
font-size: 36px;
}

.presentation {
padding: 48px 10px 28px;
text-align: center;
}

.presentation h2,
.section-entete h2 {
margin-bottom: 10px;
font-size: 26px;
}

.presentation p {
max-width: 600px;
margin: auto;
}

.decouvertes {
padding: 20px 0;
}

.section-entete {
display: flex;
align-items: center;
justify-content: space-between;
gap: 20px;
margin-bottom: 24px;
}

.lien {
color: #4f46e5;
text-decoration: none;
font-weight: 600;
}

@media (max-width: 700px) {
.accueil {
  padding: 18px;
}

.hero {
  padding: 28px 22px;
  flex-direction: column;
  align-items: flex-start;
}

.illustration {
  align-self: center;
  flex-basis: auto;
  width: 100%;
}

.section-entete {
  align-items: flex-start;
  flex-direction: column;
}
}
</style>