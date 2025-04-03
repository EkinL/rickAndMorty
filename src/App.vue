<script setup>
import { RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <header class="mb-16">
    <NavBar />
  </header>

  <RouterView />

  <Footer />
</template>
