<script setup>
const experiences = [
  {
    company: 'Hamtarot',
    role: 'Frontend Developer',
    date: '2023 - 2024',
    image: '/Hamtarot.png',
    link: 'https://hamtarot.vercel.app/',
    details: [
      'Developed a tarot card web application with randomized card generation and unique outcomes.',
      'Implemented login system with input validation and navigation logic.',
      'Designed and customized responsive UI for better user experience.',
      'Collaborated using GitHub for version control and team workflow.',
      'Tools: VS Code, Firebase, Figma',
    ],
  },
  {
    company: 'Second-Hand Camera Shop',
    role: 'DevOps Engineer Intern',
    date: 'Nov 2025 - Feb 2026',
    image: '/Second-Hand.png',
    link: 'https://websitecome.vercel.app/',
    details: [
      'Worked on production-level web application during internship program.',
      'Developed Second-Hand Camera Shop Management System.',
      'Configured PostgreSQL database using Supabase.',
      'Integrated backend with Next.js application.',
      'Implemented CI/CD pipeline using GitHub Actions.',
      'Deployed and maintained system on Vercel.',
      'Managed environment variables and production configuration.',
      'Monitored deployments and resolved integration issues.',
    ],
  },
]
</script>
<template>
  <section id="experience" class="experience">
    <div class="container">
      <span class="tag">Experience</span>
      <p class="subtitle">Here is a quick summary of my recent experiences:</p>

      <!-- Experience Card -->
      <div class="exp-card" v-for="exp in experiences" :key="exp.company">
        <!-- Left (Image + Company) -->
        <div class="exp-left">
          <img :src="exp.image" class="exp-img" />
          <h3>{{ exp.company }}</h3>
        </div>

        <!-- Center -->
        <div class="exp-center">
          <h4>{{ exp.role }}</h4>
          <ul>
            <li v-for="(item, i) in exp.details" :key="i">{{ item }}</li>
          </ul>

          <!-- 🔥 ปุ่ม -->
          <a :href="exp.link" target="_blank" class="view-btn"> View Project</a>
        </div>

        <!-- Right -->
        <div class="exp-right">
          <span>{{ exp.date }}</span>
        </div>
      </div>
    </div>
  </section>
</template>
<style scoped>
.experience {
  background: var(--bg);
  padding: 100px 20px;
}

.container {
  max-width: 900px;
  margin: auto;
  text-align: center;
}

.tag {
  background: var(--card);
  padding: 5px 12px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: 600;
}

.subtitle {
  margin-top: 15px;
  color: var(--subtext);
  font-size: 18px;
  line-height: 1.8;
  max-width: 600px;
  display: flex;
  justify-content: center;
  margin-left: auto;
  margin-right: auto;
}

/* card */
.exp-card {
  margin-top: 30px;
  background: var(--card);
  padding: 25px;
  border-radius: 12px;
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  align-items: start;
  gap: 20px;
  text-align: left;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
  border: 1px solid var(--border);
}

/* left */
.exp-left {
  text-align: center;
}

.exp-left h3 {
  color: var(--primary);
  margin: 0;
}

/* image */
.exp-img {
  width: 100%;
  height: 150px;
  object-fit: contain;
  border-radius: 10px;
  margin-bottom: 10px;
}

/* center */
.exp-center h4 {
  font-weight: 700;
  margin-bottom: 10px;
  text-align: center;
  font-size: 20px;
  line-height: 1.2;
}

.exp-center ul {
  padding-left: 18px;
}

.exp-center li {
  margin-bottom: 6px;
  font-size: 16px;
  color: var(--subtext);
  line-height: 1.6;
}

/* button */
.view-btn {
  display: inline-block;
  margin-top: 12px;
  padding: 8px 14px;
  background: #3b82f6;
  color: white;
  border-radius: 6px;
  font-size: 13px;
  text-decoration: none;
  transition: 0.3s;
}

.view-btn:hover {
  background: #2563eb;
  transform: translateY(-2px);
}

/* right */
.exp-right {
  text-align: right;
  font-size: 14px;
  color: var(--subtext);
}

/* responsive */
@media (max-width: 768px) {
  .exp-card {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .exp-right {
    text-align: center;
  }
}
</style>
