<template>
  <div class="w-full min-h-screen bg-gray-50 text-gray-900">

    <!-- Hero Section -->
    <HeroSection id="home" />

    <!-- Skills -->
    <SkillSection id="skills" />

    <!-- Projects -->
    <ProjectSection id="projects" />

    <!-- Contact -->
    <ContactSection id="contact" />

  </div>
</template>

<script setup>
import HeroSection from '@/components/home/HeroSection.vue'
import SkillSection from '@/components/home/SkillSection.vue'
import ProjectSection from '@/components/home/ProjectSection.vue'
import ContactSection from '@/components/home/ContactSection.vue'
</script>
