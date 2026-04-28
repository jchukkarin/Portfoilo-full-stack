<script setup>
import Navbar from './components/Navbar.vue'
</script>

<template>
  <div class="app-container">
    <Navbar />
  </div>
  <div class="main-container">
    <RouterView />
  </div>
</template>

<style scoped>
/* Reset ค่าพื้นฐานที่อาจติดมา */
#app {
  max-width: 100% !important;
  margin: 0 !important;
  padding: 0 !important;
  display: block !important; /* ยกเลิก grid 2 คอลัมน์ */
}

body {
  margin: 0;
  overflow-x: hidden;
}

.main-content {
  width: 100%;
}
</style>
