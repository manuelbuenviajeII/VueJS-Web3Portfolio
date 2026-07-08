<!-- src/views/App.vue -->
<template>
  <div id="app">
    <Navigation />
    <LandingSection />
    <AboutSection />
    <ToolsSection />
    <ProjectsSection />
    <ContactSection />
    <AppFooter />
  </div>
</template>

<script>
import Navigation from '@/components/Navigation.vue'
import LandingSection from '@/components/LandingSection.vue'
import AboutSection from '@/components/AboutSection.vue'
import ToolsSection from '@/components/ToolsSection.vue'
import ProjectsSection from '@/components/ProjectsSection.vue'
import ContactSection from '@/components/ContactSection.vue'
import AppFooter from '@/components/Footer.vue'

export default {
  name: 'App',
  components: {
    Navigation,
    LandingSection,
    AboutSection,
    ToolsSection,
    ProjectsSection,
    ContactSection,
    AppFooter
  }
}
</script>

<style>
@import '@/styles/main.css';

#app {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>