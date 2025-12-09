<template>
  <section
    id="contact"
    class="relative py-24 bg-gradient-to-br from-sky-900 via-sky-700 to-sky-900 overflow-hidden"
  >
    <!-- Animated Background -->
    <div class="absolute inset-0">
      <div class="absolute inset-0 opacity-20">
        <!-- BULATAN 1 -->
        <div
          class="absolute top-20 right-20 w-96 h-96 bg-sky-400 rounded-full mix-blend-multiply filter blur-3xl animate-pulse"
        ></div>

        <!-- BULATAN 2 -->
        <div
          class="absolute bottom-20 left-20 w-96 h-96 bg-blue-500 rounded-full mix-blend-multiply filter blur-3xl animate-pulse"
          style="animation-delay: 2s"
        ></div>

        <!-- BULATAN 3 -->
        <div
          class="absolute top-1/2 left-1/2 w-96 h-96 bg-cyan-400 rounded-full mix-blend-multiply filter blur-3xl animate-pulse"
          style="animation-delay: 4s"
        ></div>
      </div>
    </div>

    <!-- Grid Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div
        class="absolute inset-0"
        style="
          background-image: linear-gradient(rgba(255,255,255,0.1) 1px, transparent 1px),
          linear-gradient(90deg, rgba(255,255,255,0.1) 1px, transparent 1px);
          background-size: 50px 50px;
        "
      ></div>
    </div>

    <div class="max-w-7xl mx-auto px-8 relative z-10">
      <!-- Header -->
      <div class="text-center mb-16 space-y-6 animate-slide-up">
        <div
          class="inline-flex items-center gap-2 px-4 py-2 bg-white/10 backdrop-blur-md border border-white/20 rounded-full text-white animate-fade-in"
        >
          <Sparkles class="w-4 h-4 text-yellow-400 animate-pulse" />
          <span class="text-sm font-semibold">Let's Connect</span>
        </div>

        <h2
          class="text-5xl md:text-7xl font-extrabold bg-clip-text text-transparent 
                 bg-gradient-to-r from-white via-sky-200 to-blue-200 tracking-tight"
        >
          Get In Touch
        </h2>

        <p class="text-blue-100 text-xl max-w-2xl mx-auto leading-relaxed">
          Tertarik untuk bekerja sama? Saya siap membantu mewujudkan proyek digital Anda.
        </p>
      </div>

      <!-- CTA Banner -->
      <div
        class="mt-16 p-8 bg-gradient-to-r from-sky-600/20 to-blue-600/20 
               backdrop-blur-md border border-white/10 rounded-3xl text-center animate-fade-in"
      >
        <h3 class="text-3xl font-bold text-white mb-4">
          Ready to Start Your Project?
        </h3>

        <p class="text-blue-100 text-lg mb-6 max-w-2xl mx-auto">
          Let's collaborate and create something amazing together.
        </p>

        <div class="flex flex-wrap gap-4 justify-center">
          <a
            href="https://wa.me/6285261187956?text=Halo%20saya%20tertarik%20dengan%20jasa%20Anda"
            target="_blank"
            class="px-8 py-4 bg-gradient-to-r from-green-600 to-emerald-600 
                   text-white rounded-xl font-bold"
          >
            <MessageCircle class="w-5 h-5 inline-block" /> WhatsApp Me
          </a>

          <a
            href="#projects"
            class="px-8 py-4 bg-white/10 border border-white/20 text-white rounded-xl font-bold hover:bg-white/20"
          >
            View Portfolio
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { MessageCircle, Sparkles } from "lucide-vue-next";
</script>

<style>
/* Animations */
@keyframes slide-up {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}
@keyframes slide-left {
  from { opacity: 0; transform: translateX(-30px); }
  to { opacity: 1; transform: translateX(0); }
}
@keyframes slide-right {
  from { opacity: 0; transform: translateX(30px); }
  to { opacity: 1; transform: translateX(0); }
}
@keyframes fade-in {
  from { opacity: 0; }
  to { opacity: 1; }
}

.animate-slide-up { animation: slide-up 0.8s ease-out forwards; }
.animate-slide-left { animation: slide-left 0.8s ease-out forwards; }
.animate-slide-right { animation: slide-right 0.8s ease-out forwards; }
.animate-fade-in { animation: fade-in 0.5s ease-out forwards; }
</style>
