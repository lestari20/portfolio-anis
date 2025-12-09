<template>
  <footer class="bg-slate-900 text-gray-300 pt-16 pb-10">
    <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 md:grid-cols-3 gap-10">

      <div>
        <h2 class="text-3xl font-bold text-white mb-3">
          Anis<span class="text-blue-500">Dev</span>
        </h2>
        <p class="text-gray-400 leading-relaxed">
          Portfolio website modern dibangun dengan Vue.js dan Tailwind CSS.
        </p>
      </div>

      <div>
        <h3 class="text-xl font-semibold text-white mb-3">Navigate</h3>
        <ul class="space-y-2">
          <li><a href="#home" class="footer-link">Home</a></li>
          <li><a href="#skills" class="footer-link">Skills</a></li>
          <li><a href="#projects" class="footer-link">Projects</a></li>
          <li><a href="#contact" class="footer-link">Contact</a></li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-semibold text-white mb-3">Contact</h3>
        <ul class="space-y-2 text-gray-400">
          <li>Email: anissslestariii@gmail.com</li>
          <li>Phone: +62 852 6118 7956</li>
          <li>Location: Indonesia</li>
        </ul>
      </div>

    </div>

    <div class="border-t border-gray-700 mt-14 pt-6 text-center text-gray-500 text-sm">
      © {{ new Date().getFullYear() }} AnisDev. All rights reserved.
    </div>
  </footer>
</template>

<script setup>
</script>

<style scoped>
.footer-link {
  @apply text-gray-300 hover:text-white transition;
}
</style>
