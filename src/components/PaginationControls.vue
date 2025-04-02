<script setup>
import { ArrowLeftIcon, ArrowRightIcon } from '@heroicons/vue/24/solid'

defineProps({
  currentPage: {
    type: Number,
    required: true,
  },
  totalPages: {
    type: Number,
    required: true,
  },
})

const emit = defineEmits(['previousPage', 'nextPage'])
</script>

<template>
  <div class="fixed bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-4">
    <button
      @click="emit('previousPage')"
      :disabled="currentPage <= 1"
      class="p-3 bg-blue-500 dark:bg-blue-700 text-white rounded-full shadow-md hover:bg-blue-600 dark:hover:bg-blue-800 disabled:opacity-50 disabled:cursor-not-allowed transition-transform transform hover:scale-110"
    >
      <ArrowLeftIcon class="h-6 w-6" />
    </button>
    <button
      @click="emit('nextPage')"
      :disabled="currentPage >= totalPages"
      class="p-3 bg-blue-500 dark:bg-blue-700 text-white rounded-full shadow-md hover:bg-blue-600 dark:hover:bg-blue-800 disabled:opacity-50 disabled:cursor-not-allowed transition-transform transform hover:scale-110"
    >
      <ArrowRightIcon class="h-6 w-6" />
    </button>
  </div>
</template>
