<script setup>
import { ref } from 'vue'
import axios from 'axios'
import CharacterCard from './CharacterCard.vue'
import PaginationControls from './PaginationControls.vue'

const characters = ref([])
const currentPage = ref(1)
const totalPages = ref(0)

const fetchCharacters = (page = 1) => {
  axios
    .get(`https://rickandmortyapi.com/api/character?page=${page}`)
    .then((response) => {
      characters.value = response.data.results
      totalPages.value = response.data.info.pages
    })
    .catch((error) => {
      console.error(error)
    })
}

fetchCharacters(currentPage.value)

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    currentPage.value++
    fetchCharacters(currentPage.value)
  }
}

const previousPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--
    fetchCharacters(currentPage.value)
  }
}
</script>

<template>
  <div class="p-12 bg-gray-100 dark:bg-gray-900 min-h-screen">
    <h1 class="text-3xl font-bold text-center mb-6 text-gray-900 dark:text-white">
      Character Component
    </h1>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
      <div
        v-for="character in characters"
        :key="character.id"
        class="bg-white dark:bg-gray-800 shadow-md rounded-lg overflow-hidden transform transition hover:scale-105 hover:shadow-lg cursor-pointer"
      >
        <CharacterCard :character="character" />
      </div>
    </div>
    <PaginationControls
      :currentPage="currentPage"
      :totalPages="totalPages"
      @previousPage="previousPage"
      @nextPage="nextPage"
    />
  </div>
</template>
