<script setup>
import dropDown from './icons/dropDown.vue'
</script>

<template>
  <aside class="sidebar-container">
    <div class="users-profile">
      <div class="user-image">
        <img src="@/assets/users-image.png" alt="users-image" />
      </div>
      <div class="users-name">
        <p>Tonia Stores</p>
        <p>Fashion</p>
      </div>

      <div class="drop-down">
        <dropDown />
      </div>
    </div>

    <div class="dash-section-one">
      <div class="">
        <span>
          <svg
            width="18"
            height="18"
            viewBox="0 0 18 18"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M16.5 14.8334V9.22255C16.5 8.77043 16.408 8.32303 16.2297 7.90757C16.0513 7.49211 15.7903 7.11728 15.4625 6.80588L10.1483 1.75838C9.83858 1.46412 9.42766 1.30005 9.00042 1.30005C8.57318 1.30005 8.16225 1.46412 7.8525 1.75838L2.5375 6.80588C2.20971 7.11728 1.9487 7.49211 1.77034 7.90757C1.59198 8.32303 1.5 8.77043 1.5 9.22255V14.8334C1.5 15.2754 1.67559 15.6993 1.98816 16.0119C2.30072 16.3245 2.72464 16.5001 3.16667 16.5001H14.8333C15.2754 16.5001 15.6993 16.3245 16.0118 16.0119C16.3244 15.6993 16.5 15.2754 16.5 14.8334Z"
              stroke="#6B7280"
              stroke-width="1.66667"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </span>
      </div>

      <div class="dashboard-icon">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M14.1667 8.33329H15.8334C17.5001 8.33329 18.3334 7.49996 18.3334 5.83329V4.16663C18.3334 2.49996 17.5001 1.66663 15.8334 1.66663H14.1667C12.5001 1.66663 11.6667 2.49996 11.6667 4.16663V5.83329C11.6667 7.49996 12.5001 8.33329 14.1667 8.33329Z" stroke="#009289" stroke-width="1.3" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
  <path d="M4.16675 18.3333H5.83341C7.50008 18.3333 8.33341 17.5 8.33341 15.8333V14.1666C8.33341 12.5 7.50008 11.6666 5.83341 11.6666H4.16675C2.50008 11.6666 1.66675 12.5 1.66675 14.1666V15.8333C1.66675 17.5 2.50008 18.3333 4.16675 18.3333Z" stroke="#009289" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
  <path d="M5.00008 8.33329C6.84103 8.33329 8.33341 6.84091 8.33341 4.99996C8.33341 3.15901 6.84103 1.66663 5.00008 1.66663C3.15913 1.66663 1.66675 3.15901 1.66675 4.99996C1.66675 6.84091 3.15913 8.33329 5.00008 8.33329Z" stroke="#009289" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
  <path d="M15.0001 18.3333C16.841 18.3333 18.3334 16.8409 18.3334 15C18.3334 13.159 16.841 11.6666 15.0001 11.6666C13.1591 11.6666 11.6667 13.159 11.6667 15C11.6667 16.8409 13.1591 18.3333 15.0001 18.3333Z" stroke="#009289" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>

        <p>
          Dashboard
        </p>
      </div>
    </div>

    <div class="dash-section-two"></div>

    <div class="da"></div>
  </aside>
</template>

<style scoped>
.sidebar-container {
  background-color: #ffffff;
  grid-row: 1/-1;
}

.users-profile {
  display: grid;
  grid-template-columns: 30px 80px 1fr;
  padding-top: 2rem;
  gap: 10px;
  margin-left: 10px;
}

.users-name {
  font-size: 14px;
  line-height: 20px;
}

.users-name p:nth-child(1) {
  font-weight: 700;
}

.drop-down {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.dash-section-one,
.dash-section-two,
.dash-section-three {
  width: 80%;
  margin: 0 auto;
}

.dash-section-one {
  margin-top: 1rem;
  border-top: 1px solid #f1f3f9;
  /* margin-bottom: 2rem; */
}

.dashboard-icon {
  background-color: #F1F3F9;
  border-radius: 8px;
  display: flex;
  padding: 0.5rem;
  gap: 1rem;
}

.dashboard-icon > p {
  font-size: 14px;
  line-height: 20px;
  font-weight: 500;
}
</style>
