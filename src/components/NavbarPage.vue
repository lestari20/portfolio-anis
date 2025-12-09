<template>
  <header class="bg-white/80 backdrop-blur-md shadow sticky top-0 z-50">
    <nav class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-16">

        <!-- LEFT: Logo -->
        <div class="flex-shrink-0 flex items-center">
          <a href="#home" class="text-2xl font-bold text-blue-600 tracking-wide">
            Anis<span class="text-gray-800">Dev</span>
          </a>
        </div>

        <!-- CENTER: Desktop Menu -->
        <div class="hidden md:flex space-x-8 items-center font-medium">
          <a href="#home" class="nav-link">Home</a>
          <a href="#skills" class="nav-link">Skills</a>
          <a href="#projects" class="nav-link">Projects</a>
          <a href="#contact" class="nav-link">Contact</a>
        </div>

        <!-- RIGHT: Mobile Button -->
        <div class="md:hidden flex items-center">
          <button @click="toggleMenu" class="text-gray-700 hover:text-blue-600 transition">
            <svg
              v-if="!isOpen"
              xmlns="http://www.w3.org/2000/svg"
              class="h-7 w-7"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16" />
            </svg>

            <svg
              v-else
              xmlns="http://www.w3.org/2000/svg"
              class="h-7 w-7"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>

      </div>

      <!-- MOBILE MENU -->
      <transition name="fade">
        <div v-if="isOpen" class="md:hidden mt-2 pb-3 space-y-2">

          <!-- Auto close saat diklik -->
          <a href="#home" class="mobile-link" @click="closeMenu">Home</a>
          <a href="#skills" class="mobile-link" @click="closeMenu">Skills</a>
          <a href="#projects" class="mobile-link" @click="closeMenu">Projects</a>
          <a href="#contact" class="mobile-link" @click="closeMenu">Contact</a>

        </div>
      </transition>

    </nav>
  </header>
</template>

<script setup>
import { ref } from "vue";

const isOpen = ref(false);
const toggleMenu = () => (isOpen.value = !isOpen.value);
const closeMenu = () => (isOpen.value = false);
</script>

<style scoped>
.nav-link {
  @apply text-gray-700 hover:text-blue-600 transition-all duration-200 cursor-pointer;
}

.mobile-link {
  @apply block px-4 py-2 text-gray-700 hover:bg-gray-100 rounded-md transition cursor-pointer;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
