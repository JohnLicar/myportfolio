<script setup>
import Navbar from './components/Navbar.vue'
</script>

<template>
  <div
    class="leading-relaxed text-gray-600 dark:text-gray-300 bg-white dark:bg-gray-800 min-h-screen"
  >
    <header>
      <div>
        <Navbar />
      </div>
    </header>

    <RouterView />
  </div>
</template>
