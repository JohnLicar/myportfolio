<script setup>
import { onMounted, onUnmounted, ref } from 'vue'

const currentIndex = ref(0)
const autoplay = ref(true)
let autoplayInterval = null

const projects = [
  {
    id: 1,
    title: 'CHCDO Information System ',
    description:
      'This system, developed within the CHCDO framework, serves as a centralized repository and management tool for all information related to housing awardees under the Pabahay program. It is designed to streamline the monitoring of occupancy status, title documentation, and applicant validation processes across the organization.',
    image: '/src/assets/images/projects/chcdo_pms.png',
    technologies: ['Livewire', 'Laravel', 'MySQL', 'Tailwind CSS'],
    demoUrl: 'https://demo-ecommerce.example.com',
    githubUrl: 'https://github.com/JohnLicar/city_housing_v2/',
  },
  {
    id: 2,
    title: 'CHCDO Document Tracking System',
    description:
      'This system, developed within the CHCDO environment, facilitates the seamless tracking and monitoring of documents received from PACD. It provides a centralized platform where each document is logged upon receipt and assigned a unique identifier, enabling users to trace its journey through various stages of processing.',
    image: '/src/assets/images/projects/dts.png',
    technologies: ['Livewire', 'Laravel', 'MySQL', 'Tailwind CSS'],
    demoUrl: 'https://taskmanager-demo.example.com',
    githubUrl: 'https://github.com/JohnLicar/rmas',
  },
  {
    id: 3,
    title: 'Housing & Technical Information System',
    description:
      'The Housing & Technical Information System is a digital solution designed to modernize housing allocation processes. It serves as a centralized platform for validating potential housing awardees, maintaining comprehensive client records with scanned document verification. The system ensures transparency, reduces manual paperwork, and provides efficient tracking of applicant eligibility throughout the housing unit allocation lifecycle.',
    image: '/src/assets/images/projects/tech.png',
    technologies: ['Livewire', 'Laravel', 'MySQL', 'Tailwind CSS'],
    demoUrl: 'https://taskmanager-demo.example.com',
    githubUrl: 'https://github.com/JohnLicar/rmas',
  },
]

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % projects.length
}

const prevSlide = () => {
  currentIndex.value = currentIndex.value === 0 ? projects.length - 1 : currentIndex.value - 1
}

const goToSlide = (index) => {
  currentIndex.value = index
}

const toggleAutoplay = () => {
  autoplay.value = !autoplay.value
  if (autoplay.value) {
    startAutoplay()
  } else {
    stopAutoplay()
  }
}

const startAutoplay = () => {
  stopAutoplay()
  autoplayInterval = setInterval(nextSlide, 5000) // Change slide every 5 seconds
}

const stopAutoplay = () => {
  if (autoplayInterval) {
    clearInterval(autoplayInterval)
    autoplayInterval = null
  }
}

// Keyboard navigation
const handleKeydown = (event) => {
  if (event.key === 'ArrowLeft') {
    prevSlide()
  } else if (event.key === 'ArrowRight') {
    nextSlide()
  } else if (event.key === ' ') {
    event.preventDefault()
    toggleAutoplay()
  }
}

onMounted(() => {
  startAutoplay()
  window.addEventListener('keydown', handleKeydown)
})

onUnmounted(() => {
  stopAutoplay()
  window.removeEventListener('keydown', handleKeydown)
})
</script>

<template>
  <div class="space-y-6 py-8 px-4">
    <h1 class="text-4xl font-bold italic">Projects</h1>

    <p class="text-lg text-gray-600 dark:text-gray-300">
      Here are some of the projects I've worked on throughout my career.
    </p>
  </div>

  <section id="projects" class="py-16 bg-gray-50 dark:bg-gray-900 transition-colors duration-300">
    <div class="container mx-auto px-4">
      <!-- Carousel Container -->
      <div class="relative max-w-6xl mx-auto">
        <!-- Carousel -->
        <div class="overflow-hidden rounded-xl">
          <div
            class="flex transition-transform duration-500 ease-in-out"
            :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
          >
            <div v-for="project in projects" :key="project.id" class="w-full shrink-0 px-4">
              <div
                class="bg-white dark:bg-gray-800 rounded-2xl overflow-hidden group hover:shadow-3xl transition-all duration-500"
              >
                <!-- Project Image -->
                <div class="relative overflow-hidden">
                  <img
                    :src="project.image"
                    :alt="project.title"
                    class="w-full h-64 object-cover transition-transform duration-700 group-hover:scale-110"
                  />
                  <div
                    class="absolute inset-0 bg-linear-to-t from-black/60 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"
                  ></div>
                  <div class="absolute top-4 right-4 flex gap-2">
                    <span
                      v-for="tech in project.technologies.slice(0, 3)"
                      :key="tech"
                      class="px-3 py-1 bg-white/90 dark:bg-gray-800/90 backdrop-blur-sm rounded-full text-xs font-medium text-gray-700 dark:text-gray-200"
                    >
                      {{ tech }}
                    </span>
                  </div>
                </div>

                <!-- Project Content -->
                <div class="p-6">
                  <h3 class="text-2xl font-bold text-indigo-400 mb-2">
                    {{ project.title }}
                  </h3>
                  <p class="text-gray-600 dark:text-gray-300 mb-4 leading-relaxed">
                    {{ project.description }}
                  </p>

                  <!-- Technologies -->
                  <div class="flex flex-wrap gap-2 mb-6">
                    <span
                      v-for="tech in project.technologies"
                      :key="tech"
                      class="px-3 py-1 bg-linear-to-r from-indigo-500 to-purple-600 text-white rounded-full text-xs font-medium"
                    >
                      {{ tech }}
                    </span>
                  </div>

                  <!-- Action Buttons -->
                  <div class="flex gap-3">
                    <a
                      v-if="project.demoUrl"
                      :href="project.demoUrl"
                      target="_blank"
                      class="flex-1 bg-linear-to-r from-indigo-500 to-purple-600 text-white text-center py-3 px-4 rounded-lg font-semibold hover:from-indigo-600 hover:to-purple-700 transition-all duration-300 transform hover:-translate-y-1 shadow-lg hover:shadow-xl"
                    >
                      Live Demo
                    </a>
                    <a
                      v-if="project.githubUrl"
                      :href="project.githubUrl"
                      target="_blank"
                      class="flex-1 border-2 border-gray-300 dark:border-gray-600 text-gray-700 dark:text-gray-300 text-center py-3 px-4 rounded-lg font-semibold hover:border-indigo-500 hover:text-indigo-600 dark:hover:text-indigo-400 transition-all duration-300 transform hover:-translate-y-1"
                    >
                      View Code
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Navigation Arrows -->
        <button
          @click="prevSlide"
          class="absolute left-0 top-1/2 -translate-y-1/2 -translate-x-4 bg-white dark:bg-gray-800 w-12 h-12 rounded-full shadow-2xl flex items-center justify-center text-gray-600 dark:text-gray-300 hover:text-indigo-600 dark:hover:text-indigo-400 transition-all duration-300 hover:scale-110 border border-gray-200 dark:border-gray-700"
          :class="{ 'opacity-50 cursor-not-allowed': currentIndex === 0 }"
          :disabled="currentIndex === 0"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M15 19l-7-7 7-7"
            />
          </svg>
        </button>

        <button
          @click="nextSlide"
          class="absolute right-0 top-1/2 -translate-y-1/2 translate-x-4 bg-white dark:bg-gray-800 w-12 h-12 rounded-full shadow-2xl flex items-center justify-center text-gray-600 dark:text-gray-300 hover:text-indigo-600 dark:hover:text-indigo-400 transition-all duration-300 hover:scale-110 border border-gray-200 dark:border-gray-700"
          :class="{ 'opacity-50 cursor-not-allowed': currentIndex === projects.length - 1 }"
          :disabled="currentIndex === projects.length - 1"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M9 5l7 7-7 7"
            />
          </svg>
        </button>

        <!-- Indicators -->
        <div class="flex justify-center mt-8 gap-3">
          <button
            v-for="(project, index) in projects"
            :key="project.id"
            @click="goToSlide(index)"
            class="w-3 h-3 rounded-full transition-all duration-300"
            :class="[
              currentIndex === index
                ? 'bg-linear-to-r from-indigo-500 to-purple-600 w-8'
                : 'bg-gray-300 dark:bg-gray-600 hover:bg-gray-400 dark:hover:bg-gray-500',
            ]"
          ></button>
        </div>
      </div>

      <!-- Auto-play Toggle -->
      <div class="text-center mt-8">
        <button
          @click="toggleAutoplay"
          class="inline-flex items-center gap-2 px-4 py-2 bg-gray-200 dark:bg-gray-700 rounded-full text-sm font-medium text-gray-700 dark:text-gray-300 hover:bg-gray-300 dark:hover:bg-gray-600 transition-colors duration-300"
        >
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              v-if="autoplay"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M10 9v6m4-6v6m7-3a9 9 0 11-18 0 9 9 0 0118 0z"
            />
            <path
              v-else
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z"
            />
          </svg>
          {{ autoplay ? 'Pause Auto-play' : 'Start Auto-play' }}
        </button>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Custom scrollbar for webkit browsers */
::-webkit-scrollbar {
  width: 6px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #6366f1, #8b5cf6);
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #4f46e5, #7c3aed);
}

/* Smooth transitions */
.transition-transform {
  transition-property: transform;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

/* Hover effects */
.group:hover .group-hover\:scale-110 {
  transform: scale(1.1);
}

/* Shadow enhancements */
.shadow-3xl {
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}
</style>
