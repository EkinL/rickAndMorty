<template>
  <footer class="bg-white dark:bg-gray-900">
    <div class="mx-auto max-w-7xl px-6 py-12 md:flex md:items-center md:justify-between lg:px-8">
      <div class="flex justify-center gap-x-6 md:order-2">
        <a
          v-for="item in navigation"
          :key="item.name"
          :href="item.href"
          class="text-gray-600 hover:text-gray-800 dark:text-gray-300 dark:hover:text-white"
          target="_blank"
        >
          <span class="sr-only">{{ item.name }}</span>
          <component :is="item.icon" class="size-6" aria-hidden="true" />
        </a>
      </div>
      <p class="mt-8 text-center text-sm/6 text-gray-600 dark:text-gray-300 md:order-1 md:mt-0">
        &copy; {{ date }} Hammache Lilian, Inc. All rights reserved.
      </p>
    </div>
  </footer>
</template>

<script setup>
import { defineComponent, h } from 'vue'

const date = new Date().getFullYear()

const navigation = [
  {
    name: 'Website',
    href: 'https://www.lilianhammache.com',
    icon: defineComponent({
      render: () =>
        h(
          'svg',
          {
            fill: 'currentColor',
            viewBox: '0 0 24 24',
            xmlns: 'http://www.w3.org/2000/svg',
          },
          [
            h('path', {
              d: 'M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm6.93 6h-2.02a15.932 15.932 0 00-1.51-3.6A8.07 8.07 0 0118.93 8zM12 4c.73.97 1.31 2.19 1.68 3.6H10.3C10.69 6.19 11.27 4.97 12 4zM9.51 4.4A15.932 15.932 0 008 8H5.07a8.07 8.07 0 014.44-3.6zM4.07 10H8c-.05.66-.07 1.33-.07 2s.02 1.34.07 2H4.07A8.027 8.027 0 014.07 10zm1 6H8c.39 1.41.97 2.63 1.68 3.6A8.07 8.07 0 015.07 16zM12 20c-.73-.97-1.31-2.19-1.68-3.6h3.36C13.31 17.81 12.73 19.03 12 20zm2.49-.4c.71-.97 1.29-2.19 1.68-3.6h2.93a8.07 8.07 0 01-4.61 3.6zM20 14h-3.93c.05-.66.07-1.33.07-2s-.02-1.34-.07-2H20a8.027 8.027 0 010 4z',
            }),
          ],
        ),
    }),
  },
  {
    name: 'GitHub',
    href: 'https://github.com/EkinL',
    icon: defineComponent({
      render: () =>
        h('svg', { fill: 'currentColor', viewBox: '0 0 24 24' }, [
          h('path', {
            'fill-rule': 'evenodd',
            d: 'M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z',
            'clip-rule': 'evenodd',
          }),
        ]),
    }),
  },
  {
    name: 'LinkedIn',
    href: 'https://www.linkedin.com/in/lilian-hammache/',
    icon: defineComponent({
      render: () =>
        h(
          'svg',
          {
            fill: 'currentColor',
            viewBox: '0 0 24 24',
            xmlns: 'http://www.w3.org/2000/svg',
          },
          [
            h('path', {
              d: 'M19 0h-14c-2.76 0-5 2.24-5 5v14c0 2.76 2.24 5 5 5h14c2.76 0 5-2.24 5-5v-14c0-2.76-2.24-5-5-5zM8.34 19h-3v-9h3v9zM6.84 8.66c-.97 0-1.66-.7-1.66-1.57 0-.89.7-1.57 1.69-1.57s1.66.68 1.68 1.57c0 .87-.69 1.57-1.71 1.57zM20 19h-3v-4.8c0-1.14-.41-1.92-1.44-1.92-.79 0-1.26.53-1.47 1.04-.08.2-.1.49-.1.77v4.91h-3v-9h3v1.23c.4-.62 1.11-1.51 2.7-1.51 1.97 0 3.44 1.29 3.44 4.06v5.22z',
            }),
          ],
        ),
    }),
  },
]
</script>
