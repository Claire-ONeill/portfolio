<template>
  <section id="projects" class="project-carousel">
    <h2 class="carousel-title">My Projects</h2>
    <div class="carousel-container">
      <div
        v-for="(project, index) in projects"
        :key="index"
        class="carousel-item"
      >
        <img :src="project.image" :alt="project.title" class="project-image" />
        <div class="project-info">
          <h3 class="project-title">{{ project.title }}</h3>
          <p class="project-description">{{ project.description }}</p>
          <a :href="project.link" target="_blank" class="project-link">View Project</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ProjectCarousel",
  data() {
    return {
      projects: [
        {
          title: "Space Explorer",
          description: "A web app to explore the universe with real-time data from NASA APIs.",
          image: "/assets/space-explorer.png",
          link: "https://github.com/Claire-ONeill/space-explorer",
        },
        {
          title: "Portfolio Website",
          description: "My personal portfolio showcasing my skills and projects.",
          image: "/assets/portfolio.png",
          link: "https://github.com/Claire-ONeill/portfolio",
        },
        {
          title: "AI Chatbot",
          description: "An intelligent chatbot built with Python and NLP libraries.",
          image: "/assets/ai-chatbot.png",
          link: "https://github.com/Claire-ONeill/ai-chatbot",
        },
      ],
    };
  },
};
</script>

<style scoped>
.project-carousel {
  padding: 4rem 2rem;
  background: var(--bg-dark);
  color: var(--text-primary);
  text-align: center;
}

.carousel-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 2rem;
  text-shadow: 0 0 15px var(--glow-color);
}

.carousel-container {
  display: flex;
  gap: 2rem;
  overflow-x: auto;
  padding: 1rem;
  scroll-snap-type: x mandatory;
}

.carousel-item {
  flex: 0 0 auto;
  width: 300px;
  background: var(--bg-light);
  border-radius: 8px;
  box-shadow: var(--shadow-glow);
  scroll-snap-align: center;
  transition: transform 0.3s ease;
}

.carousel-item:hover {
  transform: scale(1.05);
}

.project-image {
  width: 100%;
  border-top-left-radius: 8px;
  border-top-right-radius: 8px;
}

.project-info {
  padding: 1rem;
}

.project-title {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.project-description {
  font-size: 1rem;
  margin-bottom: 1rem;
  color: var(--text-secondary);
}

.project-link {
  display: inline-block;
  padding: 0.5em 1em;
  background-color: var(--primary-turquoise);
  color: var(--bg-dark);
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
  box-shadow: var(--shadow-glow);
  transition: all 0.3s ease;
}

.project-link:hover {
  background-color: var(--light-turquoise);
  box-shadow: var(--shadow-glow-strong);
  transform: translateY(-2px);
}

.project-link:active {
  transform: translateY(0);
}
</style>