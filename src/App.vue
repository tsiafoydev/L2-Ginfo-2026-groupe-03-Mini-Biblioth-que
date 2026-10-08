<template>
  <div class="layout">

    <aside class="sidebar">
      <div class="logo">
        <BookOpen />
        <h1>Biblio</h1>
      </div>
      <nav class="sidebar_nav">
        <RouterLink to="/" class="menu_item">
          <House :size="18" />
          <span class="span">Acceuil</span>
        </RouterLink>

        <RouterLink to="/livres" class="menu_item">
          <Book :size="18" />
          <span class="span">Gestion des livres</span>
        </RouterLink>
      </nav>
    </aside>

    <main class="contenu">
      <div class="topbar">
        <h1>Mini bibliotheque</h1>
      </div>
      <RouterView/>
    </main>
  </div>
</template>

<script setup>
  import { ref,computed } from 'vue'
  import { BookOpen, House, Book } from 'lucide-vue-next'
  import { RouterLink } from 'vue-router'
  import { RouterView } from 'vue-router';

</script>

<style scoped>

.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  width: 240px;
  height: 100vh;
  background: #1e293b;
  color: #cbd5e1;
  padding: 24px 10px;
  display: flex;
  flex-direction: column;
  gap: 32px;
  z-index: 100;
  overflow-y: auto;
  box-sizing: border-box;
  flex-shrink: 0;
}

.logo {
    display: flex;
    align-items: center;
    gap: 10px;

    padding: 0 10px;
    margin-bottom: 30px;
}

.logo-icon {
    font-size: 28px;
}

.logo h1 {
  color: #ffffff;
  font-size: 1.6em;
  font-weight: 700;
  margin: 0;
}

.sidebar_nav {
  display: flex;
  flex-direction: column;
  gap: 7px;
  padding: 0 12px;
}

.sidebar_nav .span{
  padding: 0 10px;
}
.sidebar_nav a {
  display: block;
  padding: 12px 16px;
  border-radius: 8px;
  color: #cbd5e1;
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 500;
  transition: all 0.2s ease;
}

.sidebar_nav a:hover {
  background: rgba(255, 255, 255, 0.08);
  color: #ffffff;
}

.contenu {
  margin-left: 240px;
  flex: 1;
  min-width: 0;
  background: #f9fafb;
  padding: 0 32px 60px;
  min-height: 100vh;
}

.topbar {
  padding: 24px 0 16px;
  border-bottom: 2px solid #e5e7eb;
  margin-bottom: 24px;
}

.topbar h1 {
  color: #4f46e5;
  font-size: 1.8rem;
  font-weight: 700;
  margin: 0;
}

@media (max-width: 768px) {
  .sidebar {
    position: relative;
    width: 100%;
    height: auto;
    flex-direction: row;
    align-items: center;
    gap: 20px;
    padding: 16px;
  }

  .sidebar_nav {
    flex-direction: row;
    padding: 0;
  }

  .contenu {
    margin-left: 0;
    padding: 20px 16px 40px;
  }
}
</style>