<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }" role="navigation" aria-label="Main Navigation">
    <div class="navbar-container">
      <div class="logo">
        <router-link to="/" aria-label="Home">Claire O'Neill</router-link>
      </div>
      
      <button class="menu-toggle" @click="toggleMenu" v-if="isMobile" aria-label="Toggle Menu">
        <span></span>
        <span></span>
        <span></span>
      </button>

      <ul class="nav-menu" :class="{ active: menuOpen }" role="menu">
        <li role="menuitem"><a href="#home" @click="scrollToSection('home')">Home</a></li>
        <li role="menuitem"><a href="#about" @click="scrollToSection('about')">About</a></li>
        <li role="menuitem"><a href="#projects" @click="scrollToSection('projects')">Projects</a></li>
        <li role="menuitem"><a href="#contact" @click="scrollToSection('contact')">Contact</a></li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useRouter } from 'vue-router'

const isScrolled = ref(false)
const menuOpen = ref(false)
const isMobile = ref(false)
const router = useRouter()

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const scrollToSection = (section) => {
  menuOpen.value = false
  const element = document.getElementById(section)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const checkMobile = () => {
  isMobile.value = window.innerWidth <= 768
}

const throttle = (func, limit) => {
  let inThrottle
  return function() {
    const args = arguments
    const context = this
    if (!inThrottle) {
      func.apply(context, args)
      inThrottle = true
      setTimeout(() => (inThrottle = false), limit)
    }
  }
}

const throttledScroll = throttle(handleScroll, 100)

onMounted(() => {
  window.addEventListener('scroll', throttledScroll)
  window.addEventListener('resize', checkMobile)
  checkMobile()
})

onUnmounted(() => {
  window.removeEventListener('scroll', throttledScroll)
  window.removeEventListener('resize', checkMobile)
})
</script>

<style scoped>
.navbar {
  position: sticky;
  top: 0;
  width: 100%;
  background: transparent;
  z-index: 1000;
  transition: all 0.3s ease;
  padding: 1.5rem 0;
}

.navbar.scrolled {
  background: linear-gradient(to bottom, 
    rgba(5, 8, 16, 0.95) 0%, 
    rgba(5, 8, 16, 0.8) 100%);
  box-shadow: var(--shadow-glow);
  backdrop-filter: blur(10px);
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.logo a {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--light-turquoise);
  text-shadow: 0 0 10px var(--glow-color);
  transition: all 0.3s ease;
}

.logo a:hover {
  color: var(--primary-turquoise);
  text-shadow: 0 0 20px var(--glow-color);
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 2.5rem;
  transition: transform 0.3s ease;
}

.nav-menu li a {
  color: var(--text-secondary);
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
  padding-bottom: 0.3rem;
}

.nav-menu li a:hover {
  color: var(--light-turquoise);
}

.nav-menu li a::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--primary-turquoise);
  box-shadow: var(--shadow-glow);
  transition: width 0.3s ease;
}

.nav-menu li a:hover::after {
  width: 100%;
}

.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 0.4rem;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  box-shadow: none;
  transition: transform 0.3s ease;
}

.menu-toggle span {
  width: 25px;
  height: 3px;
  background: var(--primary-turquoise);
  border-radius: 3px;
  transition: all 0.3s ease;
}

.menu-toggle.active span:nth-child(1) {
  transform: rotate(45deg) translate(8px, 8px);
}

.menu-toggle.active span:nth-child(2) {
  opacity: 0;
}

.menu-toggle.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -7px);
}

.nav-menu.active {
  transform: translateX(0);
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .menu-toggle {
    display: flex;
  }

  .nav-menu {
    position: absolute;
    top: 70px;
    right: 0;
    flex-direction: column;
    background: rgba(5, 8, 16, 0.98);
    width: 100%;
    text-align: center;
    gap: 1.5rem;
    padding: 2rem 0;
    transform: translateX(100%);
    transition: transform 0.3s ease;
    border-top: 1px solid rgba(0, 212, 255, 0.2);
  }

  .nav-menu.active {
    transform: translateX(0);
  }

  .navbar-container {
    padding: 0 1.5rem;
  }
}
</style>
