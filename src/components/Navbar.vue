<script setup>
import { RouterLink } from 'vue-router'
import { ref, onMounted } from 'vue'

const isDark = ref(false)
const mobileOpen = ref(false)

const setTheme = (dark) => {
  isDark.value = dark
  document.documentElement.classList.toggle('dark', dark)
  localStorage.setItem('theme', dark ? 'dark' : 'light')
}

const toggleTheme = () => setTheme(!isDark.value)
const toggleMobile = () => (mobileOpen.value = !mobileOpen.value)

onMounted(() => {
  const saved = localStorage.getItem('theme')
  if (saved) {
    setTheme(saved === 'dark')
  } else {
    // Auto detect theme เครื่อง
    const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches
    setTheme(prefersDark)
  }
})
</script>

<template>
  <nav :class="['navbar', isDark ? 'dark' : 'light']">
    <div class="container">
      <RouterLink class="logo">
        <span class="circle">Portfolio</span>
      </RouterLink>

      <div class="menu">
        <a href="#home" class="menu-link">Home</a>
        <a href="#about" class="menu-link">About</a>
        <a href="#skills-section" class="menu-link">Skills</a>
        <a href="#experience" class="menu-link">Experience</a>
        <a href="#certificates" class="menu-link">Certifications</a>
        <a href="#contact" class="menu-link">Contact</a>
      </div>

      <!-- Right -->
      <div class="actions">
        <div class="toggle-container">
          <label class="switch">
            <input type="checkbox" :checked="isDark" @change="toggleTheme" />
            <span class="slider"></span>
          </label>
        </div>

        <a href="/Resume-Chukkarin.pdf" download class="btn">Download CV</a>

        <button class="mobile-btn" @click="toggleMobile" aria-label="Toggle mobile menu">
          <span class="hamburger"></span>
        </button>
      </div>
    </div>

    <div v-if="mobileOpen" class="mobile-menu">
      <a href="#home" @click="mobileOpen = false" class="mobile-link">Home</a>
      <a href="#about" @click="mobileOpen = false" class="mobile-link">About</a>
      <a href="#skills-section" @click="mobileOpen = false" class="mobile-link">Skills</a>
      <a href="#experience" @click="mobileOpen = false" class="mobile-link">Experience</a>
      <a href="#certificates" @click="mobileOpen = false" class="mobile-link">Certifications</a>
      <a href="#contact" @click="mobileOpen = false" class="mobile-link">Contact</a>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.8);
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  z-index: 1000;
  transition: all 0.3s ease;
}

.navbar.dark {
  background: rgba(0, 0, 0, 0.8);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 700;
  text-decoration: none;
  color: inherit;
  transition: transform 0.2s ease;
}

.logo:hover {
  transform: scale(1.05);
}

.circle {
  width: 150px;
  height: 40px;
  font-size: 1.2rem;
  border-radius: 20px;
  background: linear-gradient(135deg, var(--primary, #4f46e5), var(--secondary, #7c3aed));
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 15px rgba(79, 70, 229, 0.3);
  transition: all 0.3s ease;
}

.menu {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.menu-link {
  text-decoration: none;
  color: inherit;
  font-weight: 500;
  position: relative;
  transition: all 0.3s ease;
  padding: 0.5rem 1rem;
  border-radius: 8px;
}

.menu-link:hover {
  background: rgba(79, 70, 229, 0.1);
  color: var(--primary, #4f46e5);
}

.menu-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  width: 0;
  height: 2px;
  background: var(--primary, #4f46e5);
  transition: all 0.3s ease;
  transform: translateX(-50%);
}

.menu-link:hover::after {
  width: 100%;
}

.actions {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.btn {
  padding: 0.5rem 1.5rem;
  background: linear-gradient(135deg, var(--primary, #4f46e5), var(--secondary, #7c3aed));
  color: white;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(79, 70, 229, 0.3);
}

.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(79, 70, 229, 0.4);
}

.mobile-btn {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  border-radius: 8px;
  transition: background 0.3s ease;
}

.mobile-btn:hover {
  background: rgba(0, 0, 0, 0.1);
}

.hamburger {
  display: block;
  width: 24px;
  height: 2px;
  background: currentColor;
  position: relative;
  transition: all 0.3s ease;
}

.hamburger::before,
.hamburger::after {
  content: '';
  position: absolute;
  width: 24px;
  height: 2px;
  background: currentColor;
  transition: all 0.3s ease;
}

.hamburger::before {
  top: -8px;
}

.hamburger::after {
  top: 8px;
}

.mobile-menu {
  padding: 1rem 2rem;
  background: inherit;
  border-top: 1px solid rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  gap: 1rem;
  animation: slideDown 0.3s ease;
}

.mobile-link {
  text-decoration: none;
  color: inherit;
  font-weight: 500;
  padding: 0.75rem 1rem;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.mobile-link:hover {
  background: rgba(79, 70, 229, 0.1);
  color: var(--primary, #4f46e5);
}

/* Responsive */
@media (max-width: 768px) {
  .menu {
    display: none;
  }

  .mobile-btn {
    display: block;
  }

  .container {
    padding: 1rem;
  }

  .circle {
    width: 120px;
    height: 35px;
    font-size: 1rem;
  }

  .actions {
    gap: 1rem;
  }

  .btn {
    padding: 0.5rem 1rem;
    font-size: 0.9rem;
  }
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.toggle-container {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.switch {
  position: relative;
  width: 50px;
  height: 25px;
}

/* Hide default checkbox */
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  inset: 0;
  background: #ccc;
  border-radius: 25px;
  transition: 0.3s;
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.2);
}

.slider::before {
  content: '';
  position: absolute;
  height: 20px;
  width: 20px;
  left: 3px;
  top: 2.5px;
  background: white;
  border-radius: 50%;
  transition: 0.3s;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.switch input:checked + .slider {
  background: linear-gradient(135deg, var(--primary, #4f46e5), var(--secondary, #7c3aed));
}

.switch input:checked + .slider::before {
  transform: translateX(24px);
}
</style>
