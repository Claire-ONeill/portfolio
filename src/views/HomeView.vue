<script>
import NavBar from "../components/NavBar.vue";
import ParallaxBackground from "../components/ParallaxBackground.vue";
import Hero from "../components/Hero.vue";
import AboutSection from "../components/AboutSection.vue";
import ProjectCarousel from "../components/ProjectCarousel.vue";
import ContactForm from "../components/ContactForm.vue";

export default {
  components: {
    NavBar,
    ParallaxBackground,
    Hero,
    AboutSection,
    ProjectCarousel,
    ContactForm,
  },
};
</script>

<template>
  <div class="home">
    <NavBar />
    <ParallaxBackground />
    <Hero />
    <AboutSection />
    <ProjectCarousel />
    <ContactForm />
  </div>
</template>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: var(--bg-dark);
  color: var(--text-primary);
}
</style>
