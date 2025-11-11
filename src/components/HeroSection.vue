<script setup>
import HeroText from '@/components/HeroText.vue'
import SocialIcons from '@/components/SocialIcons.vue'

// Import assets
import Background from '@/assets/images/background.svg'
import Developer from '@/assets/images/developer.svg'

// Composition data
const icons = [
  { icon: 'fa-brands fa-github', link: 'https://github.com/JohnLicar' },
  { icon: 'fa-brands fa-facebook', link: 'https://facebook.com/johnlicarorion' },
  { icon: 'fa-brands fa-linkedin', link: 'https://linkedin.com/in/john-licar-orion-6806a8246/' },
  {
    icon: 'fa-solid fa-envelope',
    link: 'https://mail.google.com/mail/?view=cm&fs=1&to=johnlicarorion@gmail.com',
  },
]
</script>

<template>
  <section class="flex flex-col md:flex-row items-center justify-center min-h-[80vh] px-6 md:px-20">
    <!-- Left Image -->
    <div class="flex justify-center md:w-1/2 mb-10 md:mb-0">
      <img :src="Developer" alt="Developer illustration" class="w-72 md:w-96" />
    </div>

    <!-- Right Content -->
    <div class="relative pl-7 md:w-1/2 text-center md:text-left space-y-6">
      <!-- Background Image -->
      <img
        :src="Background"
        alt="Background abstract"
        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 opacity-10 w-[28rem] md:w-[32rem] z-0 select-none pointer-events-none"
      />

      <!-- Text -->
      <HeroText />

      <!-- Social Links -->
      <SocialIcons :icons="icons" />
    </div>
  </section>
</template>
