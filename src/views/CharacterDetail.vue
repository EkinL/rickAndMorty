<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import axios from 'axios'

const route = useRoute()
const character = ref(null)

onMounted(() => {
  const characterId = route.params.id
  axios
    .get(`https://rickandmortyapi.com/api/character/${characterId}`)
    .then((response) => {
      character.value = response.data
    })
    .catch((error) => {
      console.error(error)
    })
})
</script>

<template>
  <div v-if="character" class="p-6 bg-white dark:bg-gray-800 rounded-lg shadow-md">
    <img :src="character.image" :alt="character.name" class="w-32 h-32 rounded-full mx-auto" />
    <h2 class="text-2xl font-bold text-center text-gray-900 dark:text-white mt-4">
      {{ character.name }}
    </h2>
    <p class="text-center text-gray-600 dark:text-gray-300">Statut : {{ character.status }}</p>
    <p class="text-center text-gray-600 dark:text-gray-300">Espèce : {{ character.species }}</p>
    <p class="text-center text-gray-600 dark:text-gray-300">Genre : {{ character.gender }}</p>
    <p class="text-center text-gray-600 dark:text-gray-300">
      Origine : {{ character.origin.name }}
    </p>
    <p class="text-center text-gray-600 dark:text-gray-300">
      Dernière localisation : {{ character.location.name }}
    </p>
  </div>
  <div v-else class="text-center text-gray-500 dark:text-gray-400">Chargement...</div>
</template>
