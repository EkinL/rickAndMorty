<script setup>
import { RouterLink, RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
</script>

<template class="bg-white dark:bg-gray-800">
  <header>
    <NavBar />
  </header>

  <RouterView />
</template>
