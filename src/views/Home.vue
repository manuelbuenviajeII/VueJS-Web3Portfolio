<template>
  <div class="home">
    <Landing />
    <About />
    <Projects />
    <Tools />
    <Contact />
  </div>
</template>

<script>
import Landing from '@/components/Landing.vue'
import About from '@/components/About.vue'
import Projects from '@/components/Projects.vue'
import Tools from '@/components/Tools.vue'
import Contact from '@/components/Contact.vue'

export default {
  name: 'Home',
  components: {
    Landing,
    About,
    Projects,
    Tools,
    Contact
  }
}
</script>