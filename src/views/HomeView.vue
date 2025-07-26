<template>
  <div class="home">
    <Header />
    <Hero />
    <About />
    <Experience />
    <Projects />
    <Skills />
    <Contact />
  </div>
</template>

<script setup lang="ts">
import Header from '@/components/Header.vue'
import Hero from '@/components/Hero.vue'
import About from '@/components/About.vue'
import Experience from '@/components/Experience.vue'
import Projects from '@/components/Projects.vue'
import Skills from '@/components/Skills.vue'
import Contact from '@/components/Contact.vue'
</script>

<style scoped>
.home {
  min-height: 100vh;
}
</style>
