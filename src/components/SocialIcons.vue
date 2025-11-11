<template>
  <div class="relative flex justify-center md:justify-start gap-x-6 pt-4 z-10">
    <a
      v-for="(item, index) in icons"
      :key="index"
      :href="item.link"
      target="_blank"
      rel="noopener noreferrer"
      class="text-gray-400 hover:text-indigo-400 transition-transform duration-300 hover:scale-125 hover:rotate-3"
    >
      <i :class="item.icon"></i>
    </a>
  </div>
</template>

<script setup>
defineProps({
  icons: {
    type: Array,
    required: true,
  },
})
</script>
