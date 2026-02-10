<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'
import { RouterLink, useRoute } from 'vue-router'

const route = useRoute()
const isMenuOpen = ref(false)
const isScrolled = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20
}

const isActiveRoute = (path) => {
  return route.path === path
}

const navLinks = [
  { path: '/', label: 'Inicio' },
  { path: '/about', label: 'Nosotros' },
  { path: '/contact', label: 'Contacto' },
  { path: '/gear', label: 'Equipamiento' },
  { path: '/routes', label: 'Rutas', isCTA: true }
]

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header 
    class="navbar" 
    :class="{ 'navbar--scrolled': isScrolled, 'navbar--mobile-open': isMenuOpen }"
  >
    <div class="navbar__container">
      <RouterLink class="navbar__brand" to="/" @click="closeMenu">
        <img class="navbar__logo" src="/logo.png" alt="Logo Trekking Adventures">
        <span class="navbar__tagline">Trekking Adventures</span>
      </RouterLink>

      <nav class="navbar__nav">
        <ul class="navbar__lista">
          <li v-for="link in navLinks" :key="link.path">
            <RouterLink 
              class="navbar__rutas" 
              :class="{ 
                'navbar__rutas--active': isActiveRoute(link.path),
                'navbar__rutas--cta': link.isCTA 
              }"
              :to="link.path"
              @click="closeMenu"
            >
              {{ link.label }}
              <span class="navbar__rutas__underline"></span>
            </RouterLink>
          </li>
        </ul>
      </nav>

      <button 
        class="navbar__hamburger" 
        :class="{ 'navbar__hamburger--open': isMenuOpen }"
        @click="toggleMenu"
        aria-label="Toggle menu"
      >
        <span class="hamburger__line"></span>
        <span class="hamburger__line"></span>
        <span class="hamburger__line"></span>
      </button>
    </div>
  </header>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(245, 242, 234, 0.85);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(18, 23, 19, 0.08);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.navbar--scrolled {
  background: rgba(245, 242, 234, 0.98);
  box-shadow: 0 4px 30px rgba(12, 18, 13, 0.1);
  border-bottom: 1px solid rgba(18, 23, 19, 0.12);
}

.navbar__container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0.6rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
}

.navbar__brand {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  transition: transform 0.3s ease;
}

.navbar__brand:hover {
  transform: scale(1.02);
}

.navbar__logo {
  width: 150px;
  height: auto;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.1));
}

.navbar__tagline {
  font-family: "Space Grotesk", sans-serif;
  font-size: 0.75rem;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--color-forest, #1d2a21);
  opacity: 0.7;
  border-left: 1px solid rgba(29, 42, 33, 0.2);
  padding-left: 0.75rem;
  display: none;
}

@media (min-width: 768px) {
  .navbar__tagline {
    display: block;
  }
}

.navbar__nav {
  display: none;
}

@media (min-width: 900px) {
  .navbar__nav {
    display: block;
  }
}

.navbar__lista {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin: 0;
  padding: 0;
}

.navbar__rutas {
  position: relative;
  padding: 0.6rem 1rem;
  font-family: "Space Grotesk", sans-serif;
  font-size: 0.9rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--color-ink, #121713);
  border-radius: 8px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.navbar__rutas:hover {
  color: var(--color-forest, #1d2a21);
  background: rgba(29, 42, 33, 0.05);
}

.navbar__rutas--active {
  color: var(--color-canyon, #c46b2c);
}

.navbar__rutas__underline {
  position: absolute;
  bottom: 0;
  left: 50%;
  width: calc(100% - 1.5rem);
  height: 2px;
  background: var(--color-canyon, #c46b2c);
  transform: translateX(-50%) scaleX(0);
  transform-origin: center;
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 2px;
}

.navbar__rutas:hover .navbar__rutas__underline,
.navbar__rutas--active .navbar__rutas__underline {
  transform: translateX(-50%) scaleX(1);
}

.navbar__rutas--cta {
  background: var(--color-forest, #1d2a21);
  color: var(--color-white, #ffffff);
  padding: 0.75rem 1.5rem;
  border-radius: 999px;
  box-shadow: 0 4px 15px rgba(29, 42, 33, 0.25);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.navbar__rutas--cta:hover {
  background: var(--color-canyon, #c46b2c);
  color: var(--color-white, #ffffff);
  transform: translateY(-2px);
  box-shadow: 0 6px 25px rgba(196, 107, 44, 0.35);
}

.navbar__rutas--cta .navbar__rutas__underline {
  display: none;
}

.navbar__hamburger {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 44px;
  height: 44px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  border-radius: 8px;
  transition: background 0.3s ease;
}

@media (min-width: 900px) {
  .navbar__hamburger {
    display: none;
  }
}

.navbar__hamburger:hover {
  background: rgba(29, 42, 33, 0.05);
}

.hamburger__line {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--color-ink, #121713);
  margin: 3px 0;
  border-radius: 2px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.navbar__hamburger--open .hamburger__line:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
}

.navbar__hamburger--open .hamburger__line:nth-child(2) {
  opacity: 0;
  transform: scaleX(0);
}

.navbar__hamburger--open .hamburger__line:nth-child(3) {
  transform: translateY(-8px) rotate(-45deg);
}

/* Mobile Menu Overlay */
@media (max-width: 899px) {
  .navbar__nav {
    position: fixed;
    top: 56px;
    left: 0;
    right: 0;
    background: rgba(245, 242, 234, 0.98);
    backdrop-filter: blur(20px);
    padding: 1.5rem;
    border-bottom: 1px solid rgba(18, 23, 19, 0.12);
    box-shadow: 0 10px 40px rgba(12, 18, 13, 0.15);
    display: block;
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .navbar--mobile-open .navbar__nav {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }

  .navbar__lista {
    flex-direction: column;
    gap: 0.5rem;
  }

  .navbar__rutas {
    width: 100%;
    justify-content: center;
    padding: 1rem;
    font-size: 1rem;
  }
}
</style>
