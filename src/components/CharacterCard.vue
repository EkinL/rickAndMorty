<script setup>
const props = defineProps({
  character: {
    type: Object,
    required: true,
  },
})
</script>

<template>
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
</template>
