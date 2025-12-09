<template>
  <footer class="bg-gray-900 text-gray-300 py-12">
    <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 md:grid-cols-3 gap-10">

      <!-- 1. Brand -->
      <div>
        <h2 class="text-2xl font-bold text-white mb-3">MyBrand</h2>
        <p class="text-gray-400 leading-relaxed">
          Website modern dibangun menggunakan Vue.js dan Tailwind CSS.
        </p>
      </div>

      <!-- 2. Links -->
      <div>
        <h3 class="text-xl font-semibold text-white mb-3">Quick Links</h3>
        <ul class="space-y-2">
          <li><a href="#" class="hover:text-white">Home</a></li>
          <li><a href="#" class="hover:text-white">About</a></li>
          <li><a href="#" class="hover:text-white">Services</a></li>
          <li><a href="#" class="hover:text-white">Contact</a></li>
        </ul>
      </div>

      <!-- 3. Contact -->
      <div>
        <h3 class="text-xl font-semibold text-white mb-3">Contact</h3>
        <ul class="space-y-2">
          <li>Email: support@mybrand.com</li>
          <li>Phone: +62 812 3456 7890</li>
          <li>Location: Jakarta, Indonesia</li>
        </ul>
      </div>

    </div>

    <div class="text-center mt-10 text-gray-500 text-sm">
      © {{ new Date().getFullYear() }} MyBrand. All rights reserved.
    </div>
  </footer>
</template>

<script setup>
</script>
 