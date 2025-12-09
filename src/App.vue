<template>
  <div class="w-max-full ">
    <Navbar />

      <router-view />   
       <Footer />
    
  </div>
</template>

<script setup>
import Navbar from './components/NavbarPage.vue'
import Footer from './components/FooterPage.vue'

</script>
<style>
body {
  scroll-behavior: smooth;
}
main {
  padding-top: 100px; 
}
</style>