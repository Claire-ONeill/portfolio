<template>
  <section id="about" class="about">
    <div class="about-content">
      <h2 class="about-title">About Me</h2>
      <p class="about-description">
        Hi, I'm Claire O'Neill, a Software Engineer with a strong background in Computer Science and Data Science. I love solving complex problems and creating innovative solutions that make a difference.
      </p>
      <p class="about-description">
        With experience in building production-grade applications, I focus on writing clean, efficient, and maintainable code. I'm always eager to learn new technologies and improve my skills.
      </p>
      <a href="/ONeill_CS_resume_2023.pdf" target="_blank" class="resume-link">View My Resume</a>
    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 4rem 2rem;
  background: var(--bg-dark);
  color: var(--text-primary);
  text-align: center;
}

.about-content {
  max-width: 800px;
  margin: 0 auto;
}

.about-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 2rem;
  text-shadow: 0 0 15px var(--glow-color);
}

.about-description {
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
  color: var(--text-secondary);
}

.resume-link {
  display: inline-block;
  margin-top: 2rem;
  padding: 0.8em 1.5em;
  background-color: var(--primary-turquoise);
  color: var(--bg-dark);
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
  box-shadow: var(--shadow-glow);
  transition: all 0.3s ease;
}

.resume-link:hover {
  background-color: var(--light-turquoise);
  box-shadow: var(--shadow-glow-strong);
  transform: translateY(-2px);
}

.resume-link:active {
  transform: translateY(0);
}
</style>