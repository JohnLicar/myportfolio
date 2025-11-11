<script setup>
import { RouterLink } from 'vue-router'

defineProps({
  tag: {
    type: String,
    required: true,
  },

  link: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <RouterLink
    :to="{ name: link }"
    class="hover:text-indigo-600 outline-none transition-colors duration-300 text-gray-900 dark:text-gray-100"
    active-class=" text-indigo-400 font-semibold text-gray-900 dark:text-gray-100"
    exact-active-class="text-gray-900 dark:text-gray-100 border-b-2 border-indigo-400"
  >
    {{ tag }}
  </RouterLink>
</template>
