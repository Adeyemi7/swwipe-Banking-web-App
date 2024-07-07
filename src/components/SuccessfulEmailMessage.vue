<script setup>
import sentLogo from './icons/sentLogo.vue'
import CancelBar from './icons/CancelBar.vue'

const emit = defineEmits(['close'])

const handleClose = () => {
  emit('close')
}
</script>

<template>
  <div class="container">
    <div>
      <sentLogo />
    </div>
    <p class="message">Password reset link sent</p>

    <div>
      <CancelBar @click="handleClose" />
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
  gap: 20px;
  background-color: #ffffff;
  padding: 1em;
  border: 1px solid #95c9b4;
  border-radius: 10px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
  right: -600px;
  top: 0;
}

.message {
  margin: 0;
  color: #333;
}

/* Responsive Design */
@media (max-width: 1024px) {
  .container {
    gap: 15px;
    padding: 0.8em;
  }

  .message {
    font-size: 1rem;
  }
}

@media (max-width: 768px) {
  .container {
    gap: 10px;
    padding: 0.6em;
  }

  .message {
    font-size: 0.9rem;
  }
}

@media (max-width: 480px) {
  .container {
    gap: 8px;
    padding: 0.5em;
  }

  .message {
    font-size: 0.85rem;
  }
}

@media (max-width: 320px) {
  .container {
    gap: 5px;
    padding: 0.4em;
  }

  .message {
    font-size: 0.75rem;
  }
}
</style>
