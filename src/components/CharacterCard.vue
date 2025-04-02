<script setup>
import { useRouter } from 'vue-router'

const props = defineProps({
  character: {
    type: Object,
    required: true,
  },
})

const router = useRouter()

const goToDetail = () => {
  router.push({ name: 'CharacterDetail', params: { id: props.character.id } })
}
</script>

<template>
  <div @click="goToDetail" class="cursor-pointer">
    <div class="relative w-full h-64">
      <img
        :src="props.character.image"
        alt="Character Image"
        class="absolute inset-0 w-full h-full object-cover"
      />
    </div>
    <div class="p-4">
      <h2 class="text-xl font-semibold text-gray-800 dark:text-white">
        {{ props.character.name }}
      </h2>
      <p class="text-gray-600 dark:text-gray-300">Status: {{ props.character.status }}</p>
      <p class="text-gray-600 dark:text-gray-300">Species: {{ props.character.species }}</p>
    </div>
  </div>
</template>
