<script setup>
import { ref } from 'vue'

const images = [
  {
    src: '/certificate01.jpg',
    title: 'AI Certificate',
    desc: 'ผ่านการอบรมเกี่ยวกับ AI และ LLM',
  },
  {
    src: '/certificate02.jpg',
    title: 'Leadership Certificate',
    desc: 'ผ่านการอบรมเกี่ยวกับการนำทีมและการบริหารจัดการ',
  },
  {
    src: '/certificate03.jpg',
    title: 'DevForward Certificate',
    desc: 'ผ่านการอบรมเกี่ยวกับการพัฒนาเว็บไซต์และแอปพลิเคชัน',
  },
  {
    src: '/certificate04.jpg',
    title: 'Substance Abuse Education',
    desc: 'การศึกษาเกี่ยวกับความเสี่ยงและผลกระทบของยาเสพติด',
  },
  {
    src: '/certificate05.jpg',
    title: 'Historical City Tour',
    desc: 'การท่องเที่ยวเพื่อเรียนรู้ประวัติศาสตร์ของเมืองโบราณ',
  },
  {
    src: '/certificate06.jpg',
    title: 'Sacred Sites of Phayao',
    desc: 'การสำรวจสถานที่ศักดิ์สิทธิ์ในเขตพะเยา',
  },
]

const selectedImage = ref(null)

const openImage = (img) => {
  selectedImage.value = img.src
}

const closeImage = () => {
  selectedImage.value = null
}
</script>
<template>
  <section id="certificates" class="cert-section">
    <div class="container">
      <div class="section-title">
        <h2>Certificates</h2>
      </div>

      <p class="section-subtitle">My achievements and certifications.</p>

      <!-- GRID -->
      <div class="grid">
        <div v-for="(img, i) in images" :key="i" class="card" @click="openImage(img)">
          <img :src="img.src" />
          <div class="info">
            <h3>{{ typeof img === 'object' ? img.title : 'Certificate ' + (i + 1) }}</h3>
            <p>{{ typeof img === 'object' ? img.desc : '' }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- MODAL -->
    <div v-if="selectedImage" class="modal" @click="closeImage">
      <img :src="selectedImage" class="modal-img" />
    </div>
  </section>
</template>
<style scoped>
.section-title {
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--card);
  padding: 5px 12px;
  border-radius: 20px;
  text-align: center;
  width: fit-content;
  max-width: calc(100% - 40px);
  margin: 0 auto;
}

.section-title h2 {
  font-size: 14px;
  font-weight: 600;
}

.section-subtitle {
  margin: 15px auto 0;
  color: var(--subtext);
  text-align: center;
  font-size: 18px;
  line-height: 1.8;
  max-width: 600px;
}

.cert-section {
  padding: 80px 20px;
  background: var(--bg);
}

/* grid */
.grid {
  margin-top: 40px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}

/* card wrapper */
.card {
  padding: 12px;
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  aspect-ratio: auto; /* 🔥 ทำให้ทุกการ์ดเท่ากัน */
  background: var(--card);
}

.card img {
  max-width: 80%;
  max-height: 180px;
  object-fit: contain;
  border-radius: 8px;
  transition: transform 0.3s ease;
}

.card:hover img {
  transform: scale(1.05);
}

.info {
  padding: 16px 0 0 0;
  text-align: center;
}

.info h3 {
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 8px;
  line-height: 1.2;
}

.info p {
  font-size: 14px;
  color: var(--subtext);
  line-height: 1.6;
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
}
.modal-img {
  max-width: 80%;
  max-height: 80%;
  border-radius: 10px;
}

/* responsive */
@media (max-width: 768px) {
  .grid {
    grid-template-columns: repeat(1, 1fr);
  }

  .card img {
    height: 150px;
  }
}
</style>
