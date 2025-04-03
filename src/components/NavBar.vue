<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'
import { useRoute } from 'vue-router'
import DarkMode from './DarkMode.vue'
import SearchBar from './SearchBar.vue'

const route = useRoute()
</script>

<template>
  <Disclosure
    as="nav"
    class="bg-white dark:bg-gray-900 shadow-sm fixed top-0 w-full z-50"
    v-slot="{ open }"
  >
    <div class="mx-auto max-w-7xl px-2 sm:px-4 lg:px-8">
      <div class="flex h-16 justify-between">
        <div class="flex px-2 lg:px-0">
          <div class="flex shrink-0 items-center">
            <img
              class="h-8 w-auto"
              src="https://tailwindcss.com/plus-assets/img/logos/mark.svg?color=indigo&shade=600"
              alt="Your Company"
            />
          </div>
          <div class="hidden lg:ml-6 lg:flex lg:space-x-8">
            <RouterLink
              to="/character"
              :class="[
                'inline-flex items-center border-b-2 px-1 pt-1 text-sm font-medium',
                route.path === '/character'
                  ? 'border-indigo-500 text-gray-900 dark:text-white'
                  : 'border-transparent text-gray-500 dark:text-gray-300 hover:border-gray-300 hover:text-gray-700 dark:hover:text-gray-300',
              ]"
            >
              Character
            </RouterLink>
            <RouterLink
              to="/locations"
              :class="[
                'inline-flex items-center border-b-2 px-1 pt-1 text-sm font-medium',
                route.path === '/locations'
                  ? 'border-indigo-500 text-gray-900 dark:text-white'
                  : 'border-transparent text-gray-500 dark:text-gray-300 hover:border-gray-300 hover:text-gray-700 dark:hover:text-gray-300',
              ]"
            >
              Locations
            </RouterLink>
            <RouterLink
              to="/episodes"
              :class="[
                'inline-flex items-center border-b-2 px-1 pt-1 text-sm font-medium',
                route.path === '/episodes'
                  ? 'border-indigo-500 text-gray-900 dark:text-white'
                  : 'border-transparent text-gray-500 dark:text-gray-300 hover:border-gray-300 hover:text-gray-700 dark:hover:text-gray-300',
              ]"
            >
              Episodes
            </RouterLink>
          </div>
        </div>
        <SearchBar />
        <div class="flex items-center lg:hidden">
          <DisclosureButton
            class="relative inline-flex items-center justify-center rounded-md p-2 text-gray-400 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-700 hover:text-gray-500 dark:hover:text-white focus:ring-2 focus:ring-indigo-500 focus:outline-none focus:ring-inset"
          >
            <span class="absolute -inset-0.5" />
            <span class="sr-only">Open main menu</span>
            <Bars3Icon v-if="!open" class="block size-6" aria-hidden="true" />
            <XMarkIcon v-else class="block size-6" aria-hidden="true" />
          </DisclosureButton>
        </div>
        <DarkMode />
      </div>
    </div>

    <DisclosurePanel class="lg:hidden">
      <div class="space-y-1 pt-2 pb-3">
        <DisclosureButton
          as="a"
          href="#"
          class="block border-l-4 border-indigo-500 bg-indigo-50 dark:bg-gray-800 py-2 pr-4 pl-3 text-base font-medium text-indigo-700 dark:text-white"
        >
          Dashboard
        </DisclosureButton>
        <DisclosureButton
          as="a"
          href="#"
          class="block border-l-4 border-transparent py-2 pr-4 pl-3 text-base font-medium text-gray-600 dark:text-gray-300 hover:border-gray-300 hover:bg-gray-50 dark:hover:bg-gray-700 hover:text-gray-800 dark:hover:text-white"
        >
          Team
        </DisclosureButton>
        <DisclosureButton
          as="a"
          href="#"
          class="block border-l-4 border-transparent py-2 pr-4 pl-3 text-base font-medium text-gray-600 dark:text-gray-300 hover:border-gray-300 hover:bg-gray-50 dark:hover:bg-gray-700 hover:text-gray-800 dark:hover:text-white"
        >
          Projects
        </DisclosureButton>
        <DisclosureButton
          as="a"
          href="#"
          class="block border-l-4 border-transparent py-2 pr-4 pl-3 text-base font-medium text-gray-600 dark:text-gray-300 hover:border-gray-300 hover:bg-gray-50 dark:hover:bg-gray-700 hover:text-gray-800 dark:hover:text-white"
        >
          Calendar
        </DisclosureButton>
      </div>
    </DisclosurePanel>
  </Disclosure>
</template>
