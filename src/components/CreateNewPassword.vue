<script setup>
import { ref, reactive, computed } from 'vue'
import useVuelidate from '@vuelidate/core'
import { required, minLength, helpers } from '@vuelidate/validators'
import { sameAs } from '@vuelidate/validators'
import { useRouter } from 'vue-router'
import HandMobile from './icons/HandMobile.vue'
import SwwipeLogo from './icons/SwwipeLogo.vue'
import newPasswordCreated from './newPasswordCreated.vue'

const state = reactive({
  password: '',
  passwordRepeat: ''
})

const rules = computed(() => ({
  password: {
    required: helpers.withMessage('Please enter a valid password', required),
    minLength: minLength(6)
  },
  passwordRepeat: {
    required: helpers.withMessage('Please confirm your password', required),
    minLength: minLength(6),
    sameAs: sameAs(state.password)
  }
}))

const v$ = useVuelidate(rules, state)
const router = useRouter ()

const showPasswordCreated = ref(false)

const displayPasswordCreatedMessage = () => {
  showPasswordCreated.value = true
}

const closePasswordCreatedMessage = () => {
  showPasswordCreated.value = false
}

const handleSubmit = async (e) => {
  e.preventDefault()
  const result = await v$.value.$validate()
  if (!result) {
    console.log('Form is invalid')
    return
  }
  displayPasswordCreatedMessage(
    setTimeout(() => {
        console.log('Form is valid')
        window.location.href = '/LoginPage'
        router.push('/LoginPage')
      }, 5000)
)
  console.log('Form is valid')
}

</script>

<template>   
  <div class="container">
    <div class="logo-container">
      <SwwipeLogo />
    </div>

    <div>
          <newPasswordCreated v-if="showPasswordCreated" @close="closePasswordCreatedMessage" />
      </div>

    <div class="form-container">
      <h1>Create New Password</h1>
      <p>Create a new password to login to your account</p>

      <div class="handy">
        <HandMobile />
      </div>

      <form class="form-content">
        <div class="label-input">
          <label for="password" :class="{ error: v$.password.$error.length }"> New Password </label>
          <br />
          <input
            v-model="state.password"
            type="password"
            placeholder="Password"
            name="password"
            id="password"
          />
          <div v-for="error in v$.password.$errors" :key="error.$uid" class="error-msg">
            {{ error.$message }}
          </div>
        </div>

        <div class="label-password" :class="{ error: v$.passwordRepeat.$error.length }">
          <label for="password"> Confirm Password </label> <br />
          <input
            v-model="state.passwordRepeat"
            type="password"
            placeholder="Re-enter new password"
            name="new-password"
            id="new-password"
          />
          <div v-for="error in v$.passwordRepeat.$errors" :key="error.$uid" class="error-msg">
            {{ error.$message }}
          </div>
        </div>
        <button @click="handleSubmit">Create Password</button>
        <p class="login-texts">
          Go back to
          <router-link to="/LoginPage">
            <span>Login</span>
          </router-link>
        </p>
      </form>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 22%;
  top: 5%;
  left: 50%;
  position: absolute;
  transform: translate(-50%, 0);
  color: #20102b;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.logo-container {
  display: flex;
  justify-content: center;
  margin-bottom: 1em;
}

.handy {
  display: flex;
  align-items: center;
  justify-content: center;
}

.form-container {
  background-color: #ffffff;
  width: 100%;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
  text-align: center;
}

label {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  margin-left: 1.5em;
}

.form-content {
  margin-top: 1em;
}

.label-password {
  margin-top: 1rem;
}

input,
button {
  padding: 10px;
  margin: 8px 0;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin: 0 auto;
}

input {
  width: 85%;
}

button {
  width: 90%;
  margin-top: 3em;
  background-color: #edeef2;
  color: #9ea2b3;
  margin-bottom: 1em;
}

button:hover {
  background-color: #00b6ab;
  color: white;
}

.login-texts {
  color: #20102b;
  text-decoration: none;
}

.login-texts span {
  color: #00b6ab;
  text-decoration: none;
}

.error-msg {
  color: red;
  text-align: left;
  margin-top: 0.5em;
  margin-left: 1.5em;
}

@media (max-width: 1024px) {
  .container {
    width: 45%;
  }
}

@media (max-width: 768px) {
  .container {
    width: 60%;
  }
}

@media (max-width: 480px) {
  .container {
    width: 90%;
  }

  .form-container {
    padding: 10px;
  }
}

@media (max-width: 320px) {
  .container {
    width: 90%;
    padding: 10px;
  }

  .form-container {
    padding: 10px;
  }

  .handy svg {
    width: 80%;
  }
}
</style>
