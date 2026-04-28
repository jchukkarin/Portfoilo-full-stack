<script setup>
import { ref, computed } from 'vue'

const skills = [
  {
    name: 'Docker',
    level: 'Intermediate',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg',
  },
  {
    name: 'Kubernetes',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kubernetes/kubernetes-plain.svg',
  },
  {
    name: 'GitHub Actions',
    level: 'Intermediate',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg',
  },
  {
    name: 'AWS',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg',
  },
  {
    name: 'Cloudflare',
    level: 'CDN & Deployment',
    icon: 'https://cdn.simpleicons.org/cloudflare',
  },
  {
    name: 'argoCD',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/argocd/argocd-original.svg',
  },
  {
    name: 'Helm',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/helm/helm-original.svg',
  },
  {
    name: 'MySQL',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original-wordmark.svg',
  },
  {
    name: 'PostgreSQL',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-original-wordmark.svg',
  },
  {
    name: 'Prisma',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/prisma/prisma-original-wordmark.svg',
  },
  {
    name: 'Ubuntu',
    level: 'Basic System Usage',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/ubuntu/ubuntu-original-wordmark.svg',
  },
  {
    name: 'Tailwind CSS',
    level: 'UI Styling',
    icon: 'https://www.vectorlogo.zone/logos/tailwindcss/tailwindcss-icon.svg',
  },
  {
    name: 'Node.js',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nodejs/nodejs-original-wordmark.svg',
  },
  {
    name: 'Superbase',
    level: 'Beginner',
    icon: 'https://img.icons8.com/?size=100&id=grZaE9tjqDyr&format=png&color=000000',
  },
  {
    name: 'Vercel',
    level: 'Deployment',
    icon: 'https://img.icons8.com/?size=100&id=n61ZAjW74jZX&format=png&color=000000',
  },
  {
    name: 'Next.js',
    level: 'Intermediate',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nextjs/nextjs-original-wordmark.svg',
  },
  {
    name: 'Vue.js',
    level: 'Frontend Development',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg',
  },
  {
    name: 'Python',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original-wordmark.svg',
  },
  {
    name: 'JavaScript',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg',
  },
  {
    name: 'HTML5',
    level: 'Intermediate',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg',
  },
  {
    name: 'CSS3',
    level: 'Intermediate',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg',
  },
  {
    name: 'TypeScript',
    level: 'Beginner',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/typescript/typescript-original.svg',
  },
]

const current = ref(0)
const perPage = 5
let startX = 0
let endX = 0

const pages = computed(() => {
  const result = []
  for (let i = 0; i < skills.length; i += perPage) {
    result.push(skills.slice(i, i + perPage))
  }
  return result
})

const next = () => {
  current.value = (current.value + 1) % pages.value.length
}

const prev = () => {
  current.value = (current.value - 1 + pages.value.length) % pages.value.length
}

const handleSwipe = () => {
  const diff = startX - endX
  const threshold = 50

  if (Math.abs(diff) > threshold) {
    diff > 0 ? next() : prev()
  }
}

const handleTouchStart = (e) => {
  startX = e.touches[0].clientX
}

const handleTouchEnd = (e) => {
  endX = e.changedTouches[0].clientX
  handleSwipe()
}

const isAllView = ref(false)

const toggleView = () => {
  isAllView.value = !isAllView.value
}
</script>

<template>
  <section id="skills-section" class="skills-section">
    <div class="container">
      <div class="header">
        <span class="badge">Skills</span>
        <div class="header-content">
          <p class="font">Here are some of the technologies I've been working with:</p>
          <div>
            <button class="toggle-view" @click="toggleView">
              {{ isAllView ? 'Carousel View' : 'All Skills' }}
            </button>
          </div>
        </div>
      </div>

      <!-- Slider -->
      <div v-if="!isAllView" class="slider">
        <button class="nav prev" @click="prev">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <polyline points="15 18 9 12 15 6"></polyline>
          </svg>
        </button>
        <div
          class="slider-track"
          :style="{ transform: `translateX(-${current * 100}%)` }"
          @touchstart="handleTouchStart"
          @touchend="handleTouchEnd"
        >
          <div class="slide" v-for="(page, i) in pages" :key="i">
            <div class="skills-grid">
              <div class="skill-item" v-for="skill in page" :key="skill.name">
                <div class="circle">
                  <img :src="skill.icon" />
                </div>

                <div class="tooltip">
                  <strong>{{ skill.name }}</strong>
                  <div>
                    <span class="level">{{ skill.level }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <button class="nav next" @click="next">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <polyline points="9 18 15 12 9 6"></polyline>
          </svg>
        </button>
      </div>

      <!-- All View -->
      <div v-else class="all-view">
        <div class="skills-grid all">
          <div class="skill-item" v-for="skill in skills" :key="skill.name">
            <div class="circle">
              <img :src="skill.icon" />
            </div>

            <div class="tooltip">
              <strong>{{ skill.name }}</strong>
              <div>
                <span class="level">{{ skill.level }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Controls -->
      <div class="controls">
        <div class="dots">
          <span
            v-for="(p, i) in pages"
            :key="i"
            :class="{ active: i === current }"
            @click="current = i"
          ></span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.header {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  margin-bottom: 40px;
}

.header-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  gap: 20px;
  flex-wrap: wrap;
}

@media (max-width: 768px) {
  .header-content {
    flex-direction: column;
    align-items: center;
  }
}

.font {
  margin: 15px auto 0;
  color: var(--subtext);
  text-align: center;
  font-size: 18px;
  line-height: 1.8;
  max-width: 600px;
  width: 100%;
}

.toggle-view {
  margin-left: auto;
  background: var(--card);
  border: none;
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 14px;
  cursor: pointer;
  transition: 0.3s;
  transform: translateY(10px);
  font-weight: 600;
}

.toggle-view:hover {
  background: #2563eb;
}

/* All view grid */
.skills-grid.all {
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 30px;
}

.skills-section {
  padding: 80px 20px;
  background: var(--bg);
}

.container {
  max-width: 1100px;
  margin: auto;
  text-align: center;
}

.badge {
  display: inline-block;
  background: var(--card);
  padding: 6px 16px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: 600;
}

/* slider */
.slider {
  position: relative;
  overflow: hidden;
  margin-top: 50px;
  padding: 0 20px;
}

.slider-track {
  display: flex;
  transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: grab;
  touch-action: pan-y;
}

.slider-track:active {
  cursor: grabbing;
}

.slide {
  min-width: 100%;
  display: flex;
  justify-content: center;
  overflow: visible;
}

/* grid */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(90px, 1fr));
  gap: 25px;
  width: 100%;
  padding: 30px 0;
}

/* icon */
.circle {
  width: clamp(55px, 6vw, 80px);
  height: clamp(55px, 6vw, 80px);
  border-radius: 50%;
  background: var(--icon);
  display: flex;
  align-items: center;
  justify-content: center;
  transition:
    transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1),
    box-shadow 0.3s ease;
  will-change: transform;
  cursor: pointer;
}

.circle img {
  width: 70%;
  height: 70%;
  background: #fff;
  border-radius: 50%;
  padding: 8px;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.1));
}

/* hover */
.skill-item:hover .circle {
  transform: scale(1.2) translateY(-8px);
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.15);
}

/* tooltip */
.skill-item {
  position: relative;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-bottom: 40px;
}

.tooltip {
  position: absolute;
  bottom: -30px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--text);
  color: var(--bg);
  padding: 10px 14px;
  border-radius: 8px;
  font-size: 12px;
  font-weight: 600;
  opacity: 0;
  pointer-events: none;
  transition:
    opacity 0.25s ease,
    transform 0.25s ease;
  white-space: nowrap;
  z-index: 10;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}

.skill-item:hover .tooltip {
  opacity: 1;
  transform: translateX(-50%) translateY(-8px);
}

/* controls */
.controls {
  margin-top: -30px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px;
}

/* dots */
.dots {
  display: flex;
  gap: 8px;
}

.dots span {
  width: 6px;
  height: 6px;
  background: #d1d5db;
  border-radius: 50%;
  cursor: pointer;
  transition:
    background 0.3s ease,
    transform 0.3s ease;
}

.dots span:hover {
  transform: scale(1.2);
}

.dots span.active {
  background: #3b82f6;
  box-shadow: 0 0 8px rgba(59, 130, 246, 0.4);
}

/* responsive */
@media (max-width: 768px) {
  .header-content {
    flex-direction: column;
    align-items: center;
  }

  .toggle-view {
    margin-left: 0;
    transform: none;
    width: 100%;
    max-width: 240px;
  }
}

@media (max-width: 480px) {
  .slider {
    margin-top: 30px;
    padding: 0 10px;
  }

  .font {
    font-size: 16px;
    max-width: 100%;
    padding: 0 10px;
  }

  .badge {
    font-size: 13px;
    padding: 5px 12px;
  }

  .toggle-view {
    width: 100%;
    margin: 0 auto;
  }

  .tooltip {
    font-size: 10px;
    padding: 6px 10px;
  }
}

/* navigation buttons */
.nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 20;
  width: clamp(32px, 4vw, 44px);
  height: clamp(32px, 4vw, 44px);
  border-radius: 50%;
  border: none;
  color: var (--bg);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition:
    all 0.3s ease,
    box-shadow 0.3s ease;
}

.nav:active {
  transform: translateY(-50%) scale(0.95);
}

.nav.prev {
  left: 8px;
  transform: translateY(-100%);
}

.nav.next {
  right: 8px;
  transform: translateY(-100%);
}
</style>
