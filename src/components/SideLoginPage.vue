<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

import smart from '@/assets/Smart-handheld-pos-system.png';
import swwipe from '@/assets/Swwipe_pos_machine.png';
import mobile from '@/assets/mobile.png';

const images = [smart,mobile, swwipe];

const currentImageIndex = ref(0);

const changeImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.length;
};

let interval;
onMounted(() => {
  interval = setInterval(changeImage, 1000); // Change image every 1 second
});

onUnmounted(() => {
  clearInterval(interval);
});
</script>


<template>
  <div class="overall-container">
    <div class="main-container">
      <span class="mobile">
        <img class="phone" :src="images[currentImageIndex]" alt="mobile-image" />
      </span>

      <div class="footer">
        <h1 class="heading-text">Let your customers pay however they want</h1>

        <p class="sub-texts">
          With Swwipe every business enjoys multiple seamless, fast, and easy payments from their
          customers
        </p>

        <div class="image-texts">
          <div class="pictures">
            <p class="trio-images">
              <img src="@/assets/Ceo.png" alt="ceo-image" />
              <img src="@/assets/dev.png" alt="dev-image" />
              <img src="@/assets/Hr.png" alt="hr-image" />
            </p>
          </div>

          <span class="trio-texts">
            5000+ <br />
            <span class="sub-trio"> businesses use Swwipe </span>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

.overall-container {
  display: none;
  width: 100%;
  background-color: rgba(255, 246, 245, 1);
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.main-container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.mobile  {
  width: 90%;
  max-width: 400px;
  height:350px;
}

.phone {
  width: 100%;
  height: 100%;
  transition: opacity 1s ease-in-out;
}

/* @keyframes image-slide {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(0%);
  }
} */

.footer {
  animation: footer-slide 1s linear;
}

@keyframes footer-slide {
  0% {
    transform: translateX(-5%);
  }
  100% {
    transform: translateX(0%);
  }
}

.image-texts {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 1rem;
}

.pictures {
  display: flex;
  justify-content: center;
}

.trio-images {
  display: flex;
  align-items: center;
}

.trio-images img {
  margin-left: -1rem;
}

.trio-texts {
  margin-top: 0.5rem;
  font-size: 20px;
  font-weight: 800;
  color: #000000;
  text-align: center;
}

.sub-trio {
  color: #667085;
  font-size: 15px;
  font-weight: 400;
}

.heading-text {
  font-size: 2.625rem;
  font-weight: 800;
  line-height: 3rem;
  color: #1f2937;
  margin-top: 1rem;
}

.sub-texts {
  font-size: 1.25rem;
  font-weight: 400;
  line-height: 1.5rem;
  color: #1f2937;
  max-width: 600px;
  margin-top: 1rem;
}

@media ( width <= 654px) {
  .overall-container {
    display: none;
  }

  .main-container {
    display: none;
  }
}


@media (min-width: 768px) {
  .overall-container {
    display: flex;
  }

  .heading-text {
    font-size: 2.125rem;
    line-height: 2.5rem;
  }

  .sub-texts {
    font-size: 1.125rem;
    line-height: 1.625rem;
  }

  .mobile img {
    width: 90%;
  }
}

@media (min-width: 992px) {
  .heading-text {
    font-size: 2.375rem;
    line-height: 2.625rem;
  }

  .sub-texts {
    font-size: 1.25rem;
    line-height: 1.75rem;
  }

  .image-texts {
    flex-direction: row;
    justify-content: space-between;
  }

  .pictures {
    flex: 1;
  }

  .trio-texts {
    flex: 1;
    margin-top: 0;
    text-align: left;
    margin-left: -6rem;

  }
}

@media (min-width: 1200px) {
  .heading-text {
    font-size: 2.725rem;
    line-height: 3rem;
    text-align: left;
    width: 90%;
  }

  .sub-texts {
    font-size: 1.1rem;
    line-height: 2rem;
    text-align: left;
    width: 90%;
  }
}
</style>
