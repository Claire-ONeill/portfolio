<template>
  <section id="contact" class="contact-form">
    <h2 class="form-title">Contact Me</h2>
    <form
      action="https://formspree.io/f/your-form-id"
      method="POST"
      class="form-container"
    >
      <div class="form-group">
        <label for="name">Name</label>
        <input type="text" id="name" name="name" required />
      </div>

      <div class="form-group">
        <label for="email">Email</label>
        <input type="email" id="email" name="email" required />
      </div>

      <div class="form-group">
        <label for="message">Message</label>
        <textarea id="message" name="message" rows="5" required></textarea>
      </div>

      <button type="submit" class="submit-button">Send Message</button>
    </form>
  </section>
</template>

<style scoped>
.contact-form {
  padding: 4rem 2rem;
  background: var(--bg-dark);
  color: var(--text-primary);
  text-align: center;
}

.form-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 2rem;
  text-shadow: 0 0 15px var(--glow-color);
}

.form-container {
  max-width: 600px;
  margin: 0 auto;
  background: var(--bg-light);
  padding: 2rem;
  border-radius: 8px;
  box-shadow: var(--shadow-glow);
}

.form-group {
  margin-bottom: 1.5rem;
  text-align: left;
}

label {
  display: block;
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

input,
textarea {
  width: 100%;
  padding: 0.8rem;
  border: 1px solid var(--primary-turquoise);
  border-radius: 6px;
  font-size: 1rem;
  color: var(--text-primary);
  background: var(--bg-dark);
  box-shadow: var(--shadow-glow-inset);
}

input:focus,
textarea:focus {
  outline: none;
  border-color: var(--light-turquoise);
  box-shadow: var(--shadow-glow);
}

.submit-button {
  display: inline-block;
  padding: 0.8em 1.5em;
  background-color: var(--primary-turquoise);
  color: var(--bg-dark);
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
  box-shadow: var(--shadow-glow);
  transition: all 0.3s ease;
  border: none;
  cursor: pointer;
}

.submit-button:hover {
  background-color: var(--light-turquoise);
  box-shadow: var(--shadow-glow-strong);
  transform: translateY(-2px);
}

.submit-button:active {
  transform: translateY(0);
}
</style>