<script setup>
import { onMounted, ref } from 'vue'
import Tag from './Header/Tag.vue'

// Reactive dark mode state
const isDark = ref(false)

// Toggle between dark and light themes
const toggleDarkMode = () => {
  isDark.value = !isDark.value
  if (isDark.value) {
    document.documentElement.classList.add('dark')
    localStorage.theme = 'dark'
  } else {
    document.documentElement.classList.remove('dark')
    localStorage.theme = 'light'
  }
}

// Initialize theme from localStorage
onMounted(() => {
  if (localStorage.theme === 'dark') {
    isDark.value = true
    document.documentElement.classList.add('dark')
  }
})
</script>

<template>
  <nav class="sticky top-0 z-50 transition-colors duration-300">
    <div class="container mx-auto px-4 py-4">
      <div class="flex flex-row items-center justify-between">
        <div class="basis-1/3">
          <i class="text-7xl font-black">J</i>
          <i class="text-7xl">L</i>
          <i class="text-7xl font-black">O</i>
        </div>

        <div class="flex items-end justify-center gap-9">
          <Tag link="home" tag="Home" />
          <Tag link="about" tag="About" />
          <Tag link="about" tag="Skills" />
          <Tag link="about" tag="Project" />
          <Tag link="about" tag="Contact" />
        </div>

        <div>
          <button
            @click="toggleDarkMode"
            class="p-2 rounded-full bg-gray-200 dark:bg-gray-700 hover:scale-110 transition-transform duration-300"
          >
            <svg
              v-if="!isDark"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-6 h-6 text-yellow-500"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M12 3v1.5m0 15V21m9-9h-1.5M4.5 12H3m15.364-7.364l-1.061 1.061M6.697 17.303l-1.06 1.061M17.303 17.303l1.06 1.061M6.697 6.697l1.06 1.061M12 6.75A5.25 5.25 0 1 0 17.25 12 5.256 5.256 0 0 0 12 6.75Z"
              />
            </svg>

            <svg
              v-else
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-6 h-6 text-indigo-400"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M21.752 15.002A9.72 9.72 0 0 1 18 15.75c-5.385 0-9.75-4.365-9.75-9.75 0-1.33.266-2.597.748-3.752A9.753 9.753 0 0 0 3 11.25C3 16.635 7.365 21 12.75 21a9.753 9.753 0 0 0 9.002-5.998Z"
              />
            </svg>
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>
