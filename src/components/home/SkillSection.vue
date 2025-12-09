<template>
  <section
    class="relative py-20 bg-gradient-to-br from-slate-50 via-blue-50 to-indigo-50 overflow-hidden"
  >

    <div class="absolute inset-0 opacity-30">
      <div
        class="absolute top-20 left-10 w-72 h-72 bg-purple-300 rounded-full mix-blend-multiply filter blur-xl animate-pulse"
      ></div>
      <div
        class="absolute top-40 right-10 w-72 h-72 bg-yellow-300 rounded-full mix-blend-multiply filter blur-xl animate-pulse delay-1000"
      ></div>
      <div
        class="absolute -bottom-8 left-1/2 w-72 h-72 bg-pink-300 rounded-full mix-blend-multiply filter blur-xl animate-pulse delay-500"
      ></div>
    </div>

    <div class="relative max-w-full mx-auto px-8">

      <div class="text-center mb-16">
        <div class="inline-block mb-4">
          <span
            class="px-4 py-2 bg-indigo-100 text-indigo-700 rounded-full text-sm font-semibold"
          >
            Professional Skills
          </span>
        </div>

        <h2
          class="text-4xl md:text-5xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent mb-4"
        >
          Skills & Expertise
        </h2>

        <p class="text-gray-600 text-lg max-w-2xl mx-auto">
          Teknologi dan tools yang saya kuasai untuk membangun aplikasi web
          modern dan scalable
        </p>
      </div>

      <!-- Skills Grid -->
      <div class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-5 gap-6">
        <div
          v-for="(skill, index) in skills"
          :key="skill.name"
          class="group relative"
          @mouseenter="hoveredSkill = index"
          @mouseleave="hoveredSkill = null"
          :style="{
            animation: `fadeInUp 0.5s ease-out ${index * 0.1}s both`,
          }"
        >
          <div
            class="relative p-6 bg-white rounded-2xl shadow-lg transform transition-all duration-300 ease-out border-2 border-transparent hover:border-indigo-200"
            :class="
              hoveredSkill === index
                ? 'scale-105 shadow-2xl -translate-y-2'
                : 'hover:scale-[1.02]'
            "
          >
            <div
              class="absolute inset-0 rounded-2xl opacity-0 group-hover:opacity-100 transition-opacity duration-300"
              :class="`bg-gradient-to-br ${skill.color}`"
            ></div>

            <div class="relative z-10">
              <div
                class="mb-4 p-3 rounded-xl inline-flex text-white transform transition-transform duration-300 group-hover:scale-110 group-hover:rotate-6"
                :class="`bg-gradient-to-br ${skill.color}`"
              >
                <component :is="skill.icon" class="w-8 h-8" />
              </div>

              <h3
                class="font-bold text-xl mb-2 text-gray-800 group-hover:text-white transition-colors duration-300"
              >
                {{ skill.name }}
              </h3>

              <div class="mb-2">
                <span
                  class="px-3 py-1 text-xs font-semibold rounded-full bg-gray-100 text-gray-700 group-hover:bg-white/20 group-hover:text-white transition-colors"
                >
                  {{ skill.level }}
                </span>
              </div>

              <p class="text-sm text-gray-600 group-hover:text-white/90 transition-colors">
                {{ skill.description }}
              </p>

              <div class="mt-4 h-1.5 bg-gray-200 rounded-full overflow-hidden group-hover:bg-white/30">
                <div
                  class="h-full rounded-full transition-all duration-1000 ease-out"
                  :class="`bg-gradient-to-r ${skill.color}`"
                  :style="{ width: hoveredSkill === index ? '100%' : '0%' }"
                ></div>
              </div>
            </div>

            <div
              class="absolute inset-0 rounded-2xl overflow-hidden opacity-0 group-hover:opacity-100 transition-opacity"
            >
              <div
                class="absolute inset-0 bg-gradient-to-r from-transparent via-white/20 to-transparent transform -skew-x-12 -translate-x-full group-hover:translate-x-full transition-transform duration-1000"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import {
  Code2,
  Server,
  Database,
  Palette,
  Zap,
  Layout,
  Globe,
} from "lucide-vue-next";

const hoveredSkill = ref(null);

const skills = [
  {
    name: "Vue.js",
    icon: Layout,
    color: "from-emerald-400 to-teal-500",
    level: "Advanced",
    description: "Progressive JavaScript Framework",
  },
  {
    name: "Node.js",
    icon: Server,
    color: "from-green-400 to-emerald-500",
    level: "Advanced",
    description: "Backend Runtime Environment",
  },
  {
    name: "Express",
    icon: Zap,
    color: "from-gray-400 to-gray-600",
    level: "Advanced",
    description: "Fast minimalist web framework",
  },
  {
    name: "MariaDB",
    icon: Database,
    color: "from-green-500 to-green-700",
    level: "Intermediate",
    description: "Relational database, fork dari MySQL",
  },
  {
    name: "MySQL",
    icon: Database,
    color: "from-blue-400 to-blue-600",
    level: "Advanced",
    description: "Popular relational database",
  },
  {
    name: "TailwindCSS",
    icon: Palette,
    color: "from-cyan-400 to-blue-500",
    level: "Advanced",
    description: "Utility-first CSS framework",
  },
  {
    name: "REST API",
    icon: Globe,
    color: "from-purple-400 to-pink-500",
    level: "Intermediate",
    description: "API development & integration",
  },
  {
    name: "JavaScript",
    icon: Code2,
    color: "from-yellow-400 to-orange-500",
    level: "Advanced",
    description: "Modern ES6+ programming",
  },
  {
    name: "PHP",
    icon: Code2,
    color: "from-gray-600 to-gray-400",
    level: "Junior",
    description: "Backend scripting language",
  },
  {
    name: "UI/UX Design",
    icon: Palette, 
    color: "from-blue-600 to-sky-300",
    level: "Advanced",
    description: "Mendesain tampilan dan pengalaman pengguna yang intuitif, modern, dan responsif.",
  },
];
</script>

<style>
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
</style>
