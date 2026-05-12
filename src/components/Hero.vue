<template>
  <section id="home" class="hero">
    <div class="hero-content">
      <h1 class="hero-title">Claire O'Neill</h1>
      <p class="hero-subtitle">Software Engineer | CS & Data Science</p>
      <p class="hero-description">
        Passionate about building clean, efficient, and innovative solutions.
      </p>
      <button class="cta-button" @click="scrollToSection('about')">Learn More</button>
    </div>
  </section>
</template>

<script setup>
const scrollToSection = (section) => {
  const element = document.getElementById(section)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
.hero {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(to bottom, var(--bg-dark), var(--bg-darker));
  text-align: center;
  color: var(--text-primary);
}

.hero-content {
  max-width: 800px;
  padding: 2rem;
}

.hero-title {
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 1rem;
  text-shadow: 0 0 20px var(--glow-color);
}

.hero-subtitle {
  font-size: 1.5rem;
  font-weight: 500;
  margin-bottom: 1.5rem;
  color: var(--text-secondary);
}

.hero-description {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  color: var(--text-muted);
}

.cta-button {
  background-color: var(--primary-turquoise);
  color: var(--bg-dark);
  border: none;
  padding: 0.8em 1.5em;
  font-size: 1rem;
  font-weight: 600;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: var(--shadow-glow);
}

.cta-button:hover {
  background-color: var(--light-turquoise);
  box-shadow: var(--shadow-glow-strong);
  transform: translateY(-2px);
}

.cta-button:active {
  transform: translateY(0);
}
</style>