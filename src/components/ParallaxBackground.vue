<template>
  <div class="parallax-container">
    <div class="stars" :style="{ transform: `translateY(${scrollY * 0.5}px)` }">
      <div 
        v-for="star in stars" 
        :key="star.id"
        class="star"
        :style="{ 
          left: star.x + '%',
          top: star.y + '%',
          width: star.size + 'px',
          height: star.size + 'px',
          opacity: star.opacity,
          animation: `twinkle ${star.duration}s infinite ${star.delay}s`
        }"
      ></div>
    </div>

    <div class="planets-container">
      <div 
        v-for="planet in planets"
        :key="planet.id"
        class="planet-wrapper"
        :style="{ 
          left: planet.x + '%',
          top: planet.y + '%',
          '--parallax-offset': (planet.parallax * scrollY) + 'px'
        }"
        @mouseenter="hoveredPlanet = planet.id"
        @mouseleave="hoveredPlanet = null"
      >
        <div class="planet" :class="{ hovered: hoveredPlanet === planet.id }">
          <div class="planet-inner" :style="{ backgroundColor: planet.color }"></div>
        </div>
        <div v-if="hoveredPlanet === planet.id" class="planet-tooltip">
          {{ planet.fact }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const scrollY = ref(0)
const hoveredPlanet = ref(null)
const stars = ref([])
const planets = ref([])

const generateStars = () => {
  const starArray = []
  for (let i = 0; i < 100; i++) {
    starArray.push({
      id: i,
      x: Math.random() * 100,
      y: Math.random() * 100,
      size: Math.random() * 2 + 0.5,
      opacity: Math.random() * 0.7 + 0.3,
      duration: Math.random() * 3 + 2,
      delay: Math.random() * 5
    })
  }
  return starArray
}

const generatePlanets = () => {
  const planetArray = [
    {
      id: 1,
      x: 10,
      y: 20,
      size: 80,
      color: '#00d4ff',
      parallax: 0.3,
      fact: '💻 Built 5+ production apps'
    },
    {
      id: 2,
      x: 70,
      y: 35,
      size: 120,
      color: '#9d4edd',
      parallax: 0.2,
      fact: '🎓 CS + Data Science Major'
    },
    {
      id: 3,
      x: 30,
      y: 60,
      size: 100,
      color: '#3a86ff',
      parallax: 0.25,
      fact: '🚀 Always learning & growing'
    },
    {
      id: 4,
      x: 80,
      y: 75,
      size: 70,
      color: '#00d4ff',
      parallax: 0.28,
      fact: '✨ Passionate about clean code'
    },
    {
      id: 5,
      x: 15,
      y: 80,
      size: 90,
      color: '#00f0ff',
      parallax: 0.22,
      fact: '🎯 Problem solver & innovator'
    }
  ]
  return planetArray
}

const handleScroll = () => {
  scrollY.value = window.scrollY
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
  stars.value = generateStars()
  planets.value = generatePlanets()
  window.addEventListener('scroll', throttledScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', throttledScroll)
})
</script>

<style scoped>
.parallax-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: radial-gradient(ellipse at center, #1a1a3e 0%, #0a0e27 50%, #050810 100%);
  overflow: hidden;
  z-index: -1;
}

.stars {
  position: absolute;
  width: 100%;
  height: 100%;
  will-change: transform;
}

.star {
  position: absolute;
  background: radial-gradient(circle, #ffffff, rgba(255, 255, 255, 0.3));
  border-radius: 50%;
}

@keyframes twinkle {
  0%, 100% {
    opacity: 0.3;
  }
  50% {
    opacity: 1;
  }
}

.planets-container {
  position: absolute;
  width: 100%;
  height: 100%;
}

.planet-wrapper {
  position: absolute;
  transform: translateY(var(--parallax-offset));
  will-change: transform;
  cursor: pointer;
}

.planet {
  position: relative;
  width: 100px;
  height: 100px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  transform: translateX(-50%);
}

.planet.hovered {
  transform: scale(1.2);
  box-shadow: 0 0 40px rgba(0, 212, 255, 0.8);
}

.planet-inner {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  box-shadow: 
    inset -2px -2px 4px rgba(0, 0, 0, 0.4),
    0 0 20px rgba(0, 212, 255, 0.4),
    0 0 40px rgba(0, 212, 255, 0.2);
  position: relative;
  overflow: hidden;
}

.planet-inner::before {
  content: '';
  position: absolute;
  top: 10%;
  left: 10%;
  width: 30%;
  height: 30%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.4), transparent);
  border-radius: 50%;
}

.planet-tooltip {
  position: absolute;
  bottom: -50px;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0, 212, 255, 0.9);
  color: var(--bg-dark);
  padding: 0.5rem 1rem;
  border-radius: 4px;
  white-space: nowrap;
  font-size: 0.9rem;
  font-weight: 500;
  box-shadow: var(--shadow-glow-strong);
  animation: slideUp 0.3s ease;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateX(-50%) translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }
}

@media (max-width: 768px) {
  .star {
    display: none;
  }

  .planet-wrapper {
    opacity: 0.7;
  }

  .planet {
    width: 60px;
    height: 60px;
  }
}
</style>
