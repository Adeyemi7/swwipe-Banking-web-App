<script setup>
import topNavigation from './topNavigation.vue'
</script>

<template>
  <div class="main-content">
    <topNavigation />
    <div class="content">
      <div class="section section-wide">
        <h2 class="title">Welcome, Tolani</h2>
        <div class="dashboard-overview">
          <div class="overview-item">
            <p>Amount collected</p>
            <h3>₦0.00</h3>
          </div>
          <div class="overview-item">
            <p>Total Payment</p>
            <h3>$198,298</h3>
          </div>
          <div class="overview-item">
            <p>Total Withdrawal</p>
            <h3>$198,298</h3>
          </div>
        </div>
      </div>
      <div class="section payment-channels">
        <h2 class="title">Payment Channels</h2>
        <img class="phone" src="@/assets/mobile.png" alt="mobile-image" />

      </div>

      <div class="section recent-payments">
        <h2 class="title">Recent Payments</h2>
        <div class="payment">
          <span>USSD</span>
          <span>July 22, 9:42 PM</span>
          <span>+₦2,000</span>
          <span>Successful</span>
        </div>
        <div class="payment">
          <span>USSD</span>
          <span>July 22, 9:42 PM</span>
          <span>+₦2,000</span>
          <span>Successful</span>
        </div>
      </div>
      <div class="section payment-overview">
        <h2 class="title">Payment Overview</h2>
      </div>
    </div>
  </div>
</template>



<style scoped>
.main-content {
  margin-left: 250px;
  display: flex;
  flex-direction: column;
  height: 100vh;  /* background-color: green !important; */
}

.content {
  flex-grow: 1;
  overflow-y: auto;
  padding: 50px;
  display: grid;
  grid-template-columns: 1.5fr 1.5fr 1.5fr;
  grid-template-rows: auto auto;
  gap: 15px;
  background-color: #E4E5E7;
}

.section {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.section-wide {
  grid-column: span 2;
}

.title {
  margin: 0 0 20px;
  font-weight: bold;
}

.recent-payments .payment {
  display: flex;
  justify-content: space-between;
  padding: 10px 0;
  border-bottom: 1px solid #f0f0f0;
}

.recent-payments .payment:last-child {
  border-bottom: none;
}

.payment-channels {
  background-color: bisque;
  grid-row: 1/3;
  grid-column: 3/4;
}

</style>
