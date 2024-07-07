<script setup>
import LoginData from '@/components/LoginData.vue'
import SideLoginPage from '@/components/SideLoginPage.vue'

// setTimeout(() => {
//   this.$router.push('/LoginPage')
// }, 5000)
</script>

<template>
  <div class="app-container">
    <LoginData />
    <SideLoginPage />
  </div>
</template>

<style scoped>
.app-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

@media (max-width: 41em) {
  .app-container {
    width: 100%;
    grid-template-columns: 1fr;
  }
}


</style>
