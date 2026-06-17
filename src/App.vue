<script setup>
import { ref } from 'vue'
import HomePage from '@/pages/HomePage.vue'
import BusinessPage from '@/pages/BusinessPage.vue'


const currentPage = ref('home')
const currentSlug = ref('')

const navigateTo = (pageName, slug = '') => {
  currentPage.value = pageName
  if (slug) {
    currentSlug.value = slug
  }
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<template>
  <div class="app-container">
    <keep-alive>
      <component :is="currentPage === 'home' ? HomePage : BusinessPage" :slug="currentSlug" @navigate="navigateTo" />
    </keep-alive>
  </div>
</template>

<style>
/* Ajout d'une transition simple entre les pages pour un effet professionnel */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>