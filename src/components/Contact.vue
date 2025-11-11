<script setup>
import Contact from '@/assets/images/contact.svg'
</script>

<template>
  <div class="space-y-6 py-8 px-4">
    <h1 class="text-4xl font-bold italic">Let's Connect</h1>

    <p class="text-lg text-gray-600 dark:text-gray-300">
      Have a question or a project in mind? Drop a message!
    </p>
  </div>

  <section class="flex flex-col md:flex-row items-center justify-center min-h-[80vh] px-6 md:px-20">
    <!-- Left Image -->
    <div class="flex justify-center md:w-1/2 mb-10 md:mb-0">
      <img :src="Contact" alt="Developer illustration" class="w-72 md:w-96" />
    </div>

    <div class="w-full md:w-1/2 space-y-6">
      <div class="space-y-4">
        <div class="flex items-center space-x-3">
          <i class="lucide lucide-phone text-xl"></i>
          <span>+639655998518</span>
        </div>
        <div class="flex items-center space-x-3">
          <i class="lucide lucide-mail text-xl"></i>
          <span>johnlicarorion@gmail.com</span>
        </div>
        <div class="flex items-center space-x-3">
          <i class="lucide lucide-user text-xl"></i>
          <span>John Licar Orion</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped></style>
