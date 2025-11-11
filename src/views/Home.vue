<script setup>
import AboutView from '@/components/About.vue'
import Contact from '@/components/Contact.vue'
import HeroSection from '@/components/HeroSection.vue'
import Projects from '@/components/Projects.vue'
import Skills from '@/components/Skills.vue'
</script>

<template>
  <HeroSection class="animate-fade-in-up" id="hero" />
  <AboutView id="about" />
  <Skills />
  <Projects />
  <Contact />
</template>
