<script setup>
import topNavigation from '@/components/topNavigation.vue'
import sideBar from '@/components/sideBar.vue'
import mainDashBoard from '@/components/mainDashBoard.vue'
</script>

<template>
  <div class="app-container">
    <topNavigation />
    <sideBar />
    <mainDashBoard />
  </div>
</template>

<style scoped>

.app-container {
  display: grid;
  height: 100vh;
  grid-template-columns: 14rem 1fr ;
  grid-template-rows: auto 1fr;
  background-color: #F1F3F9;
}

</style>
