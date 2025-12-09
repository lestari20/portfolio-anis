<template>
  <section
    class="relative min-h-screen flex items-center overflow-hidden 
           bg-gradient-to-br from-sky-900 via-sky-700 to-sky-900"
  >
    <!-- Background Grid -->
    <div class="absolute inset-0 opacity-20">
      <div
        class="absolute inset-0"
        :style="{
          backgroundImage:
            'linear-gradient(rgba(56,189,248,0.15) 1px, transparent 1px), linear-gradient(90deg, rgba(56,189,248,0.15) 1px, transparent 1px)',
          backgroundSize: '50px 50px'
        }"
      />
    </div>

    <!-- Floating Orbs -->
    <div class="absolute inset-0 overflow-hidden">
      <div
        class="absolute w-96 h-96 bg-sky-400/30 rounded-full blur-3xl animate-pulse"
        :style="{
          top: '10%',
          left: '10%',
          transform: `translate(${mouse.x * 0.02}px, ${mouse.y * 0.02}px)`
        }"
      ></div>

      <div
        class="absolute w-96 h-96 bg-blue-300/30 rounded-full blur-3xl animate-pulse"
        :style="{
          bottom: '10%',
          right: '10%',
          animationDelay: '1s',
          transform: `translate(${mouse.x * -0.02}px, ${mouse.y * -0.02}px)`
        }"
      ></div>

      <div
        class="absolute w-72 h-72 bg-cyan-300/20 rounded-full blur-3xl animate-pulse"
        :style="{
          top: '50%',
          left: '50%',
          animationDelay: '2s',
          transform: `translate(${mouse.x * 0.01}px, ${mouse.y * 0.01}px)`
        }"
      ></div>
    </div>

    <!-- Main Content -->
    <div class="relative z-10 w-full max-w-full mx-auto px-8 lg:px-24 py-20">
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- LEFT CONTENT -->
        <div class="space-y-8">
          <!-- Greeting Badge -->
          <div
            class="inline-flex items-center gap-2 px-4 py-2 bg-white/10 backdrop-blur-md 
                   border border-white/20 rounded-full text-white animate-fade-in"
          >
            <!-- <span class="text-yellow-300 animate-pulse text-sm">✨</span> -->
            <span class="text-sm font-medium">Welcome to my portfolio</span>
          </div>

          <!-- Heading -->
          <div class="space-y-4">
            <h1 class="text-5xl lg:text-7xl font-bold leading-tight animate-slide-up">
              <span class="text-white">Hi, I'm</span><br />
              <span
                class="bg-gradient-to-r from-sky-300 via-blue-400 to-cyan-300 
                       bg-clip-text text-transparent animate-gradient"
              >
                Anis Lestari
              </span>
            </h1>

            <!-- Rotating Role -->
            <div class="flex items-center gap-3 text-2xl lg:text-3xl font-semibold text-sky-200">
              <!-- <span class="text-sky-400 text-3xl">💻</span> -->
              <span class="animate-fade-in" :key="rolesIndex">{{ roles[rolesIndex] }}</span>
            </div>
          </div>

          <!-- Description -->
          <p
            class="text-lg lg:text-xl text-sky-100 max-w-xl leading-relaxed animate-slide-up"
            style="animation-delay: 0.2s"
          >
            I build modern and scalable web apps — specializing in
            <span class="text-sky-300 font-semibold">frontend</span>,
            <span class="text-blue-300 font-semibold">backend</span>, and
            <span class="text-cyan-300 font-semibold">clean UX</span>.
          </p>

          <!-- Tech Pills -->
          <div class="flex flex-wrap gap-3 animate-slide-up" style="animation-delay:0.3s">
            <span
              v-for="(tech, i) in techs"
              :key="tech"
              class="px-4 py-2 bg-white/5 backdrop-blur-sm border border-white/10 
                     rounded-lg text-sm text-sky-100 hover:bg-white/10 
                     hover:border-sky-400/50 transition-all duration-300"
              :style="{ animationDelay: `${0.4 + i * 0.1}s` }"
            >
              {{ tech }}
            </span>
          </div>

          <!-- Buttons -->
          <div class="flex flex-wrap gap-4 animate-slide-up" style="animation-delay:0.5s">
            <a
              href="#projects"
              class="group px-8 py-4 bg-gradient-to-r from-sky-500 to-blue-600 text-white 
                     rounded-xl font-semibold shadow-lg hover:scale-105 transition-all 
                     flex items-center gap-2"
            >
              View My Work →
            </a>

            <a
              href="#contact"
              class="px-8 py-4 bg-white/10 backdrop-blur-md border border-white/20 text-white 
                     rounded-xl font-semibold hover:bg-white/20 transition-all flex items-center gap-2"
            >
              ✉ Contact Me
            </a>
          </div>

          <!-- Social -->
          <!-- <div class="flex gap-4 animate-slide-up" style="animation-delay:0.6s">
            <a class="p-3 bg-white/5 border border-white/10 rounded-lg text-sky-100 hover:bg-white/10">
              🌐
            </a>
            <a class="p-3 bg-white/5 border border-white/10 rounded-lg text-sky-100 hover:bg-white/10">
              🔗
            </a>
            <a class="p-3 bg-white/5 border border-white/10 rounded-lg text-sky-100 hover:bg-white/10">
              ✉
            </a>
          </div> -->
        </div>

        <!-- RIGHT CONTENT (Code Box) -->
        <div class="hidden lg:block relative">
          <div class="relative w-full h-[600px] animate-float">
            <div
              class="absolute inset-0 bg-gradient-to-br from-white/10 to-white/5 backdrop-blur-xl 
                     border border-white/20 rounded-3xl p-8 shadow-2xl"
            >
              <div class="space-y-3 font-mono text-sm">
                <div class="text-sky-300">const developer = {</div>
                <div class="pl-4 text-blue-300">
                  name: <span class="text-green-300">'Anis Lestari'</span>,
                </div>
                <div class="pl-4 text-blue-300">
                  role: <span class="text-green-300">'Fullstack Dev'</span>,
                </div>
                <div class="pl-4 text-blue-300">skills: ['Vue.js','Node.js'],</div>
                <div class="text-sky-300">}</div>
              </div>

              <div
                class="absolute -top-8 -right-8 w-24 h-24 bg-sky-300/30 rounded-2xl 
                       backdrop-blur-sm border border-white/10 flex items-center justify-center 
                       animate-bounce-slow"
              >
                <span class="text-3xl text-white">💠</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 animate-bounce">
      <div class="w-6 h-10 border-2 border-white/30 rounded-full flex justify-center">
        <div class="w-1.5 h-3 bg-white/50 rounded-full mt-2 animate-scroll"></div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";

const mouse = ref({ x: 0, y: 0 });
const rolesIndex = ref(0);

const roles = [
  "Fullstack Developer",
  "UI/UX ",
  "Grapic Design"
];

const techs = ["Vue.js", "Node.js", "TailwindCSS", "mysql sequelize"];

onMounted(() => {
  window.addEventListener("mousemove", (e) => {
    mouse.value = { x: e.clientX, y: e.clientY };
  });

  setInterval(() => {
    rolesIndex.value = (rolesIndex.value + 1) % roles.length;
  }, 3000);
});
</script>

<style>
@keyframes gradient {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

.animate-gradient {
  animation: gradient 3s ease infinite;
  background-size: 200% 200%;
}

@keyframes slide-up {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

.animate-slide-up {
  animation: slide-up 0.8s ease forwards;
  opacity: 0;
}

@keyframes fade-in {
  from { opacity: 0; }
  to { opacity: 1; }
}

.animate-fade-in { animation: fade-in 0.5s ease forwards; }

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-20px); }
}

.animate-float { animation: float 6s infinite ease-in-out; }

@keyframes bounce-slow {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

.animate-bounce-slow { animation: bounce-slow 3s infinite ease-in-out; }

@keyframes scroll {
  0% { transform: translateY(0); opacity: 0; }
  50% { opacity: 1; }
  100% { transform: translateY(12px); opacity: 0; }
}

.animate-scroll { animation: scroll 2s infinite ease-in-out; }
</style>
