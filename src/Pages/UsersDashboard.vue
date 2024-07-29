<script setup>
import sideBar from '@/components/sideBar.vue';
import mainDashBoard from '@/components/mainDashBoard.vue';
</script>

<template>
  <div class="dashboard">
    <sideBar />
    <mainDashBoard />
  </div>
</template>


<style scoped>
.dashboard {
  display: flex;
}
</style>
