<script setup>
import { defineEmits, ref, reactive, computed } from 'vue'
import useVuelidate from '@vuelidate/core'
import { required, email, helpers } from '@vuelidate/validators'
import CancelBar from './icons/CancelBar.vue'
import HandMobile from './icons/HandMobile.vue'
import SuccessfulEmailMessage from './SuccessfulEmailMessage.vue'
import { useRouter } from 'vue-router'

const state = reactive({
  email: ''
})

const rules = computed(() => ({
  email: {
    required: helpers.withMessage('Please enter a valid email address with @ symbol', required),
    email
  }
}))

const v$ = useVuelidate(rules, state)
const router = useRouter() // Initialize useRouter to use for navigation


const emit = defineEmits(['close'])

const showForgotPassword = ref(false)

const displaySuccessfulMessage = () => {
  showForgotPassword.value = true
}

const closeSuccessfulMessage = () => {
  showForgotPassword.value = false
}

const handleClose = () => {
  emit('close')
}


const handleForgotPassword = async (e) => {
  e.preventDefault()
  const result = await v$.value.$validate()
  if (!result) {
    console.log('Form is invalid')
    return
  }
  displaySuccessfulMessage(
    setTimeout(() => {
        console.log('Form is valid')
        router.push('/PasswordReset')
      }, 5000)

)
  console.log('Form is valid')
}

</script>

<template>
  <div class="overlay">
    <div class="pop-up">
      <div v-if="showForgotPassword">
          <SuccessfulEmailMessage @close="closeSuccessfulMessage" />
        </div>
        
      <div class="bar">
        <CancelBar @click="handleClose" />
      </div>
      <div class="password-texts">
        <p class="forget-text">Forgot Password</p>
        <p class="forget-description">
          Don’t worry, it happens. Please provide the email address associated with your account.
        </p>
        <div class="handy">
          <HandMobile />
        </div>
        <div class="label-input" :class="{ error: v$.email.$errors.length }">
          <label for="email-address">Email Address</label>
          <input
            type="email"
            placeholder="sammymetaverse@gmail.com"
            name="email-address"
            id="email-address"
            v-model="state.email"
          />
          <div v-for="error in v$.email.$errors" :key="error.$uid" class="error-msg">
            {{ error.$message }}
          </div>
        </div>
        <div class="btn-submit">
          <button @click="handleForgotPassword" class="btn" type="submit">Submit</button>
        </div>
        <p class="inbox-text">
          Can’t find the link in your inbox? Check your spam folder or
          <span @click="handleForgotPassword" class="inbox-link">Resend link</span>
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.overlay {
  background-color: rgba(75, 85, 99, 0.6);
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  position: fixed;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.pop-up {
  background-color: #ffffff;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
  width: 90%;
  max-width: 500px;
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  position: relative;
}

.bar {
  display: flex;
  justify-content: flex-end;
}

.password-texts {
  color: #1f2937;
}

.forget-text {
  font-size: 20px;
  font-weight: 700;
  margin-bottom: 10px;
}

.forget-description {
  font-size: 16px;
  font-weight: 500;
  margin-bottom: 20px;
}

.handy {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
}

.label-input {
  margin-bottom: 20px;
}

.label-input label {
  display: block;
  text-align: left;
  margin-bottom: 5px;
}

input {
  width: 95%;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

.btn-submit {
  margin-bottom: 20px;
}

.btn {
  width: 100%;
  padding: 10px;
  background-color: #edeef2;
  color: #9ea2b3;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.btn:hover {
  background-color: #00b6ab;
  color: white;
}

.inbox-text {
  margin-top: 10px;
}

.inbox-link {
  color: #00b6ab;
  cursor: pointer;
}

.error-msg {
  color: red;
  text-align: left;
  margin-top: 5px;
}

@media (max-width: 600px) {
  .pop-up {
    width: 80%;
    padding: 10px;
  }
  .header {
    flex-direction: column;
  }
  .header h2 {
    margin-top: 10px;
  }
}
</style>
