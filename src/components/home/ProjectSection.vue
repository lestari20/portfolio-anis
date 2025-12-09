<template>
  <section
    id="projects"
    class="relative py-24 bg-gradient-to-br from-sky-900 via-sky-700 to-sky-900 overflow-hidden"
  >
    <!-- Animated Background -->
    <div class="absolute inset-0">
      <div class="absolute inset-0 opacity-20">
        <div
          class="absolute top-20 left-20 w-96 h-96 bg-blue-500 rounded-full mix-blend-multiply filter blur-3xl animate-pulse"
        ></div>
        <div
          class="absolute bottom-20 right-20 w-96 h-96 bg-purple-500 rounded-full mix-blend-multiply filter blur-3xl animate-pulse"
          style="animation-delay: 2s"
        ></div>
        <div
          class="absolute top-1/2 left-1/2 w-96 h-96 bg-pink-500 rounded-full mix-blend-multiply filter blur-3xl animate-pulse"
          style="animation-delay: 4s"
        ></div>
      </div>
    </div>

    <!-- Grid Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div
        class="absolute inset-0"
        style="
          background-image: linear-gradient(rgba(255, 255, 255, 0.1) 1px,
              transparent 1px),
            linear-gradient(90deg, rgba(255, 255, 255, 0.1) 1px,
              transparent 1px);
          background-size: 50px 50px;
        "
      ></div>
    </div>

    <div class="max-w-7xl mx-auto px-6 relative z-10">
      <!-- Header -->
      <div
        class="text-center mb-16 space-y-6 transition-all duration-1000"
        :class="isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'"
      >
        <div
          class="inline-flex items-center gap-2 px-4 py-2 bg-white/10 backdrop-blur-md border border-white/20 rounded-full text-white"
        >
          <Sparkles class="w-4 h-4 text-yellow-400 animate-pulse" />
          <span class="text-sm font-semibold">Portfolio Projects</span>
        </div>

        <!-- <h2
          class="text-5xl md:text-7xl font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-white via-blue-200 to-purple-200 tracking-tight"
        >
          Featured Projects
        </h2>

        <p class="text-gray-300 text-lg max-w-3xl mx-auto leading-relaxed">
          Eksplorasi koleksi proyek inovatif yang dikembangkan dengan teknologi
          terkini dan standar industri terbaik
        </p> -->
      </div>

      <!-- Search -->
      <div
        class="max-w-2xl mx-auto mb-12 transition-all duration-1000 delay-200"
        :class="isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'"
      >
        <div class="relative">
          <Search
            class="absolute left-4 top-1/2 -translate-y-1/2 w-5 h-5 text-gray-400"
          />
          <input
            type="text"
            v-model="searchTerm"
            placeholder="Search projects by name or description..."
            class="w-full pl-12 pr-4 py-4 bg-white/10 backdrop-blur-md border border-white/20 rounded-2xl text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent"
          />
          <button
            v-if="searchTerm"
            @click="searchTerm = ''"
            class="absolute right-4 top-1/2 -translate-y-1/2 text-gray-400 hover:text-white"
          >
            ✕
          </button>
        </div>
      </div>

      <!-- Filter Buttons -->
      <div
        class="flex flex-wrap justify-center gap-3 mb-16 transition-all duration-1000 delay-300"
        :class="isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'"
      >
        <button
          v-for="cat in categories"
          :key="cat"
          @click="selectedCategory = cat"
          class="group px-6 py-3 rounded-xl font-semibold transition-all duration-300 transform hover:scale-105 flex items-center gap-2"
          :class="
            selectedCategory === cat
              ? 'bg-gradient-to-r from-blue-600 to-purple-600 text-white shadow-lg shadow-purple-500/50'
              : 'bg-white/10 backdrop-blur-md border border-white/20 text-white hover:bg-white/20'
          "
        >
          <component :is="getCategoryIcon(cat)" v-if="cat !== 'All'" class="w-4 h-4" />
          <span>{{ cat }}</span>

          <span
            class="px-2 py-0.5 rounded-full text-xs"
            :class="
              selectedCategory === cat ? 'bg-white/20' : 'bg-white/10'
            "
          >
            {{ getProjectCount(cat) }}
          </span>
        </button>
      </div>

      <!-- Projects Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(project, index) in filteredProjects"
          :key="project.id"
          class="group relative bg-white/5 backdrop-blur-md rounded-2xl overflow-hidden border border-white/10 hover:border-purple-500/50 transition-all duration-500 transform hover:-translate-y-2 hover:shadow-2xl hover:shadow-purple-500/20"
          :style="`animation: fadeInUp 0.6s ease-out ${index * 0.1}s both`"
        >
          <!-- IMAGE -->
          <div class="relative h-64 overflow-hidden bg-gradient-to-br from-gray-800 to-gray-900">
            <img
              :src="project.image"
              :alt="project.title"
              class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
              @error="e => e.target.src = fallbackImg"
            />

            <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/50 to-transparent opacity-60 group-hover:opacity-80 transition-opacity"></div>

            <!-- Category Badge -->
            <div
              class="absolute top-4 left-4 px-3 py-1.5 rounded-full text-xs font-bold shadow-lg backdrop-blur-sm text-white flex items-center gap-1.5 transform transition-transform group-hover:scale-110"
              :class="`bg-gradient-to-r ${project.badgeColor}`"
            >
              <component :is="getCategoryIcon(project.category)" class="w-4 h-4" />
              <span>{{ project.category }}</span>
            </div>

            <!-- Hover View Button -->
            <div
              class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-all bg-black/60 backdrop-blur-sm"
            >
              <a
                :href="project.link"
                target="_blank"
                class="px-6 py-3 bg-white text-gray-900 rounded-xl font-bold transform scale-90 group-hover:scale-100 hover:bg-gradient-to-r hover:from-blue-600 hover:to-purple-600 hover:text-white flex items-center gap-2"
              >
                <ExternalLink class="w-4 h-4" />
                View Live
              </a>
            </div>

            <!-- Tech Pills -->
            <div
              class="absolute bottom-4 left-4 right-4 flex flex-wrap gap-2 opacity-0 group-hover:opacity-100 transition-opacity"
            >
              <span
                v-for="tech in project.tech"
                :key="tech"
                class="px-2 py-1 bg-white/90 text-gray-900 text-xs font-semibold rounded-md"
              >
                {{ tech }}
              </span>
            </div>
          </div>

          <!-- CONTENT -->
          <div class="p-6 space-y-4">
            <h3
              class="text-2xl font-bold text-white group-hover:text-transparent group-hover:bg-clip-text group-hover:bg-gradient-to-r group-hover:from-blue-400 group-hover:to-purple-400 transition-all line-clamp-1"
            >
              {{ project.title }}
            </h3>

            <p
              class="text-gray-400 leading-relaxed line-clamp-3 min-h-[72px] group-hover:text-gray-300"
            >
              {{ project.desc }}
            </p>

            <div class="pt-4 border-t border-white/10 flex items-center justify-between">
              <a
                :href="project.link"
                target="_blank"
                class="inline-flex items-center gap-2 text-blue-400 font-semibold hover:text-purple-400 hover:gap-3 transition-all"
              >
                Explore
                <ExternalLink class="w-4 h-4" />
              </a>

              <component
                :is="getCategoryIcon(project.category)"
                class="text-2xl opacity-50 group-hover:opacity-100 transition-opacity"
                :class="getCategoryColor(project.category)"
              />
            </div>
          </div>

          <!-- Corner Decoration -->
          <div
            class="absolute top-0 right-0 w-20 h-20 bg-gradient-to-br from-purple-500/20 to-blue-500/20 rounded-bl-full transform translate-x-10 -translate-y-10 group-hover:translate-x-0 group-hover:translate-y-0 transition-transform"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted } from "vue";

// ICONS
import {
  ExternalLink,
  Search,
  Sparkles,
  Code,
  ShoppingCart,
  Building2,
  Network,
  Settings,
} from "lucide-vue-next";

const isVisible = ref(false);
onMounted(() => {
  setTimeout(() => (isVisible.value = true), 200);
});

// fallback image
const fallbackImg =
  "https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=800&h=600&fit=crop";

// =====================
//     PROJECT DATA
// =====================
const projects = ref([
  {
    id: 1,
    title: "Melody V2 Main System",
    category: "System",
    badgeColor: "bg-gradient-to-r from-purple-500 to-purple-700",
    desc: "Sistem utama Melody V2 dengan fitur lengkap dan tampilan modern.",
    link: "https://melodyv2.phisoft.co.id/",
    image: new URL("@/assets/melodyv2.png", import.meta.url).href,
    tech: ["Vue.js", "Node.js", "MySQL"],
  },
  {
    id: 2,
    title: "E-commerce 1",
    category: "E-commerce",
    badgeColor: "bg-gradient-to-r from-blue-500 to-blue-700",
    desc: "E-commerce modern dengan UI clean dan fitur lengkap.",
    link: "https://melodyv2.phisoft.co.id/ecommerce1/",
    image: new URL("@/assets/ecommerce1.png", import.meta.url).href,
    tech: ["Vue.js", "TailwindCSS", "API"],
  },
  {
    id: 3,
    title: "E-commerce 2",
    category: "E-commerce",
    badgeColor: "bg-gradient-to-r from-blue-500 to-blue-700",
    desc: "Platform e-commerce profesional dengan tampilan elegan.",
    link: "https://melodyv2.phisoft.co.id/ecommerce2/",
    image: new URL("@/assets/ecommerce2.png", import.meta.url).href,
    tech: ["Vue.js", "Express", "MongoDB"],
  },
  {
    id: 4,
    title: "E-commerce 3",
    category: "E-commerce",
    badgeColor: "bg-gradient-to-r from-blue-500 to-blue-700",
    desc: "E-commerce stylish dengan navigasi yang smooth.",
    link: "https://melodyv2.phisoft.co.id/ecommerce3/",
    image: new URL("@/assets/ecommerce3.png", import.meta.url).href,
    tech: ["Vue.js", "REST API", "CSS3"],
  },
  {
    id: 5,
    title: "Sewa Mobil Platform",
    category: "E-commerce",
    badgeColor: "bg-gradient-to-r from-blue-500 to-blue-700",
    desc: "Sistem penyewaan mobil profesional.",
    link: "https://compro.pasifiksgroup.com:8443/sewa%20mobil%201.4/",
    image: new URL("@/assets/sewamobil.png", import.meta.url).href,
    tech: ["Vue.js", "Node.js", "MySQL"],
  },
  {
    id: 6,
    title: "Phisoft Company Profile",
    category: "Compro",
    badgeColor: "bg-gradient-to-r from-green-500 to-green-700",
    desc: "Website company profile profesional.",
    link: "https://www.phisoft.co.id",
    image: new URL("@/assets/compro-phisoft.png", import.meta.url).href,
    tech: ["Vue.js", "TailwindCSS", "SEO"],
  },
  {
    id: 7,
    title: "Senyaman Group",
    category: "Compro",
    badgeColor: "bg-gradient-to-r from-green-500 to-green-700",
    desc: "Website profile Senyaman Group.",
    link: "https://compro.pasifiksgroup.com:8443/senyaman-Group/",
    image: new URL("@/assets/senyaman group.png", import.meta.url).href,
    tech: ["Vue.js", "Animation", "Responsive"],
  },
  {
    id: 8,
    title: "Senyaman Living",
    category: "Compro",
    badgeColor: "bg-gradient-to-r from-green-500 to-green-700",
    desc: "Company profile hunian modern.",
    link: "https://compro.pasifiksgroup.com:8443/Senyaman%20Living%201.2/",
    image: new URL("@/assets/senyaman living.png", import.meta.url).href,
    tech: ["Vue.js", "UI/UX", "Interactive"],
  },
  {
    id: 9,
    title: "MLM System",
    category: "MLM",
    badgeColor: "bg-gradient-to-r from-red-500 to-red-700",
    desc: "Sistem MLM modern dengan dashboard profesional.",
    link: "https://melodyv2.phisoft.co.id/mlm1/",
    image: new URL("@/assets/mlm.png", import.meta.url).href,
    tech: ["Vue.js", "Node.js", "Real-time"],
  },
  {
    id: 10,
    title: "Back Office System",
    category: "System",
    badgeColor: "bg-gradient-to-r from-purple-500 to-purple-700",
    desc: "Back office dengan modul terintegrasi.",
    link: "#",
    image: new URL("@/assets/back office.png", import.meta.url).href,
    tech: ["Vue.js", "Express", "Dashboard"],
  },
  {
    id: 11,
    title: "Compro 1",
    category: "Compro",
    badgeColor: "bg-gradient-to-r from-green-500 to-green-700",
    desc: "Template company profile elegan dari Melody.",
    link: "https://melodyv2.phisoft.co.id/compro1/",
    image: "http://apicompro.phisoft.co.id/uploads/1761743047624-compro1.jpeg"
  },
  {
    id: 12,
    title: "Compro 2",
    category: "Compro",
    badgeColor: "bg-gradient-to-r from-green-500 to-green-700",
    desc: "Desain modern untuk website perusahaan.",
    link: "https://melodyv2.phisoft.co.id/compro2/",
    image: "http://apicompro.phisoft.co.id/uploads/1761743051885-compro2.jpeg"
  },
  {
    id: 13,
    title: "Compro 3",
    category: "Compro",
    badgeColor: "bg-gradient-to-r from-green-500 to-green-700",
    desc: "Website company profile dengan tampilan estetik.",
    link: "https://melodyv2.phisoft.co.id/compro3/",
    image: "http://apicompro.phisoft.co.id/uploads/1761743056312-compro3.jpeg"
  },
  {
    id: 14,
    title: "Compro 4",
    category: "Compro",
    badgeColor: "bg-gradient-to-r from-green-500 to-green-700",
    desc: "Situs profile perusahaan versi modern.",
    link: "https://melodyv2.phisoft.co.id/compro4/",
    image: "http://apicompro.phisoft.co.id/uploads/1761884766442-compro4.jpeg"
  },
  {
    id: 15,
    title: "Compro 5",
    category: "Compro",
    badgeColor: "bg-gradient-to-r from-green-500 to-green-700",
    desc: "Website business profile tipe corporate.",
    link: "https://melodyv2.phisoft.co.id/compro9/",
    image: "http://apicompro.phisoft.co.id/uploads/1762508685139-compro9.jpeg"
  },
  
]);

// State
const selectedCategory = ref("All");
const searchTerm = ref("");

// Categories
const categories = computed(() => [
  "All",
  ...new Set(projects.value.map((p) => p.category)),
]);

// Filter
const filteredProjects = computed(() =>
  projects.value.filter((p) => {
    const matchCat =
      selectedCategory.value === "All" ||
      p.category === selectedCategory.value;
    const matchSearch =
      p.title.toLowerCase().includes(searchTerm.value.toLowerCase()) ||
      p.desc.toLowerCase().includes(searchTerm.value.toLowerCase());
    return matchCat && matchSearch;
  })
);

// Count
const getProjectCount = (cat) => {
  if (cat === "All") return projects.value.length;
  return projects.value.filter((p) => p.category === cat).length;
};

// Icons mapping
const getCategoryIcon = (cat) => {
  const icons = {
    System: Settings,
    "E-commerce": ShoppingCart,
    Compro: Building2,
    MLM: Network,
  };
  return icons[cat] || Code;
};

// Colors
const getCategoryColor = (cat) => {
  const colors = {
    System: "text-purple-600",
    "E-commerce": "text-blue-600",
    Compro: "text-green-600",
    MLM: "text-red-600",
  };
  return colors[cat] || "text-gray-600";
};
</script>


<style>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>