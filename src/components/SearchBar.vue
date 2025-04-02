<script setup>
import { ref, watch } from 'vue'
import { useRouter } from 'vue-router'
import axios from 'axios'
import { MagnifyingGlassIcon } from '@heroicons/vue/20/solid'

const searchTerm = ref('')
const searchResults = ref([])
const router = useRouter()

// Fonction pour rechercher des personnages en fonction du terme de recherche
const searchCharacters = async (query) => {
  if (query.length === 0) {
    searchResults.value = []
    return
  }
  try {
    const response = await axios.get(`https://rickandmortyapi.com/api/character/?name=${query}`)
    searchResults.value = response.data.results
  } catch (error) {
    console.error('Erreur lors de la recherche de personnages:', error)
    searchResults.value = []
  }
}

// Surveille les changements du terme de recherche et effectue la recherche
watch(searchTerm, (newQuery) => {
  searchCharacters(newQuery)
})

// Navigue vers la page de détails du personnage sélectionné
const goToCharacterDetail = (id) => {
  router.push({ name: 'CharacterDetail', params: { id }, force: true })
  searchTerm.value = ''
  searchResults.value = []
}
</script>

<template>
  <div class="relative flex flex-1 items-center justify-center px-2 lg:ml-6 lg:justify-end">
    <div class="grid w-full max-w-lg grid-cols-1 lg:max-w-xs">
      <input
        v-model="searchTerm"
        type="search"
        name="search"
        class="col-start-1 row-start-1 block w-full rounded-md bg-white dark:bg-gray-700 py-1.5 pr-3 pl-10 text-base text-gray-900 dark:text-white outline-1 -outline-offset-1 outline-gray-300 dark:outline-gray-600 placeholder:text-gray-400 dark:placeholder:text-gray-300 focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6"
        placeholder="Rechercher un personnage..."
      />
      <MagnifyingGlassIcon
        class="pointer-events-none col-start-1 row-start-1 ml-3 size-5 self-center text-gray-400 dark:text-gray-300"
        aria-hidden="true"
      />
    </div>
    <ul
      v-if="searchResults.length > 0"
      class="absolute top-full mt-1 w-full max-w-lg bg-white dark:bg-gray-700 rounded-md shadow-lg z-10"
    >
      <li
        v-for="character in searchResults"
        :key="character.id"
        @click="goToCharacterDetail(character.id)"
        class="cursor-pointer px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:text-white text-gray-900 dark:text-gray-300"
      >
        {{ character.name }}
      </li>
    </ul>
  </div>
</template>
