<script setup>
import {
  CssIcon,
  DigitalOceanIcon,
  DockerIcon,
  FigmaIcon,
  GitHubIcon,
  GitIcon,
  Html5Icon,
  JavaScriptIcon,
  LaravelIcon,
  LivewireIcon,
  MySqlIcon,
  NodeDotjsIcon,
  PhpIcon,
  TailwindCssIcon,
  VueDotjsIcon,
} from 'vue3-simple-icons'

import { computed, ref } from 'vue'

// Icons (you can replace these with your preferred icon library)

const activeCategory = ref('All')

const categories = ['All', 'Frontend', 'Backend', 'Tools', 'Design']

const skillsData = [
  // Frontend
  { name: 'HTML5', level: 95, category: 'Frontend', icon: Html5Icon, iconColor: 'text-orange-500' },
  { name: 'CSS3', level: 90, category: 'Frontend', icon: CssIcon, iconColor: 'text-blue-500' },
  {
    name: 'Livewire',
    level: 90,
    category: 'Frontend',
    icon: LivewireIcon,
    iconColor: 'text-pink-400',
  },
  {
    name: 'JavaScript',
    level: 88,
    category: 'Frontend',
    icon: JavaScriptIcon,
    iconColor: 'text-yellow-500',
  },
  {
    name: 'Vue.js',
    level: 85,
    category: 'Frontend',
    icon: VueDotjsIcon,
    iconColor: 'text-green-500',
  },

  {
    name: 'Tailwind CSS',
    level: 90,
    category: 'Frontend',
    icon: TailwindCssIcon,
    iconColor: 'text-cyan-500',
  },

  // Backend
  {
    name: 'Node.js',
    level: 82,
    category: 'Backend',
    icon: NodeDotjsIcon,
    iconColor: 'text-green-600',
  },
  {
    name: 'Laravel',
    level: 90,
    category: 'Backend',
    icon: LaravelIcon,
    iconColor: 'text-orange-500',
  },
  { name: 'PHP', level: 75, category: 'Backend', icon: PhpIcon, iconColor: 'text-purple-800' },
  { name: 'MySQL', level: 80, category: 'Backend', icon: MySqlIcon, iconColor: 'text-blue-700' },

  // Tools
  { name: 'Docker', level: 75, category: 'Tools', icon: DockerIcon, iconColor: 'text-blue-500' },
  { name: 'Git', level: 88, category: 'Tools', icon: GitIcon, iconColor: 'text-orange-600' },

  {
    name: 'DigitalOcean',
    level: 75,
    category: 'Tools',
    icon: DigitalOceanIcon,
    iconColor: 'text-blue-500',
  },
  {
    name: 'GitHub',
    level: 85,
    category: 'Tools',
    icon: GitHubIcon,
    iconColor: 'text-gray-800 dark:text-white',
  },

  { name: 'Figma', level: 75, category: 'Tools', icon: FigmaIcon, iconColor: 'text-purple-600' },
]

const skills = computed(() => {
  if (activeCategory.value === 'All') {
    return skillsData
  }
  return skillsData.filter((skill) => skill.category === activeCategory.value)
})
</script>

<template>
  <div class="space-y-6 py-8 px-4">
    <h1 class="text-4xl font-bold italic">Skill</h1>

    <p class="text-lg text-gray-600 dark:text-gray-300">
      Here are the list of tools that I have used throughout my career.
    </p>
  </div>

  <!-- Categories Tabs (Optional) -->
  <div class="mt-12">
    <div class="flex flex-wrap justify-center gap-2 mb-8">
      <button
        v-for="category in categories"
        :key="category"
        @click="activeCategory = category"
        :class="[
          'px-4 py-2 rounded-full text-sm font-medium transition-all duration-300',
          activeCategory === category
            ? 'bg-indigo-600 text-white shadow-lg'
            : 'bg-gray-100 dark:bg-gray-800 text-gray-600 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-gray-700',
        ]"
      >
        {{ category }}
      </button>
    </div>
  </div>

  <!-- Skills Grid -->
  <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-6">
    <div
      v-for="(skill, index) in skills"
      :key="skill.name"
      class="smooth-card bg-white dark:bg-gray-800 rounded-xl p-6 text-center shadow-lg hover:shadow-2xl transition-all duration-500 ease-out transform hover:-translate-y-3 border border-gray-100 dark:border-gray-700 group"
      :style="{ animationDelay: `${index * 0.1}s` }"
    >
      <div class="mb-4 flex justify-center">
        <component :is="skill.icon" class="w-8 h-8" :class="skill.iconColor" />
      </div>
      <h3 class="text-lg font-semibold text-gray-800 dark:text-white mb-3">{{ skill.name }}</h3>
      <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2 mb-2 overflow-hidden">
        <div
          class="h-full bg-gradient-to-r from-indigo-500 to-purple-600 rounded-full transition-all duration-1000 ease-out"
          :style="{ width: skill.level + '%' }"
        ></div>
      </div>
      <span class="text-sm text-gray-600 dark:text-gray-400 font-medium">{{ skill.level }}%</span>
    </div>
  </div>
</template>

<style scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fillBar {
  from {
    width: 0%;
  }
}

.smooth-card {
  /* Enhanced smooth hover effects */
  transition:
    transform 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94),
    box-shadow 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94),
    border-color 0.3s ease,
    background-color 0.3s ease;

  /* Subtle scale effect */
  transform: translateZ(0);
  backface-visibility: hidden;
  perspective: 1000px;
}

.smooth-card:hover {
  transform: translateY(-12px) scale(0.9) translateZ(0);
  box-shadow:
    0 25px 50px -12px rgba(0, 0, 0, 0.25),
    0 0 0 1px rgba(99, 102, 241, 0.1);
  border-color: rgba(99, 102, 241, 0.2);
}

/* Optional: Add a subtle gradient overlay on hover */
.smooth-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.03) 0%, rgba(168, 85, 247, 0.03) 100%);
  border-radius: inherit;
  opacity: 0;
  transition: opacity 0.5s ease;
  pointer-events: none;
}

.smooth-card:hover::before {
  opacity: 1;
}
</style>
