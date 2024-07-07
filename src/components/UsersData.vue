<script setup>
import { reactive, computed } from 'vue'
import { useVuelidate } from '@vuelidate/core'
import { required, email, minLength, maxLength, helpers } from '@vuelidate/validators'
import { sameAs } from '@vuelidate/validators'
import SwwipeLogo from './icons/SwwipeLogo.vue'
import { useRouter } from 'vue-router' // Import useRouter from Vue Router

const state = reactive({
  password: '',
  passwordRepeat: '',
  email: '',
  businessName: ''
})

const rules = computed(() => ({
  password: {
    required: helpers.withMessage('Please enter a valid password', required),
    minLength: minLength(8),
    maxLength: maxLength(20)
  },
  passwordRepeat: {
    required: helpers.withMessage('Please confirm your password', required),
    sameAs: sameAs(state.password)
  },
  email: {
    required: helpers.withMessage('Please enter a valid email address', required),
    email
  },
  businessName: {
    required: helpers.withMessage('Business name must be provided', required),
    minLength: minLength(6)
  }
}))

const v$ = useVuelidate(rules, state)
const router = useRouter() // Initialize useRouter to use for navigation

const handleSubmit = async (e) => {
  e.preventDefault()
  const result = await v$.value.$validate()
  if (!result) {
    console.log('Form is invalid')
    return
  }
  console.log('Form is valid')

  // Redirect or navigate to another route using Vue Router
  router.push('/LoginPage') // Example of using router.push to navigate to '/LoginPage'
}
</script>


<template>
  <div class="real-container">
    <div class="logo-container">
      <SwwipeLogo class="s-logo" />
    </div>

    <section class="login-details">
      <div>
        <p class="Create-texts">Create a Swwipe account</p>
        <p class="header-texts">Start receiving payments for your business</p>
      </div>

      <form @submit="handleSubmit" class="registration-inputs">
        <div class="label-input" :class="{ error: v$.businessName.$errors.length }">
          <label for="business-name"> Business Name </label> 
          <input
            type="text"
            v-model="state.businessName"
            placeholder="Enter Business Name"
            name="business-name"
            id="business-name"
          />
          <div v-for="error in v$.businessName.$errors" :key="error.$uid" class="error-msg">
            {{ error.$message }}
          </div>
        </div>

        <div class="label-input" :class="v$.email.$errors.length">
          <label for="email-address"> Email Address </label>
          <input
            type="email"
            placeholder="Enter Email Address"
            name="email-address"
            id="email-address"
            v-model="state.email"
          />
          <div v-for="error in v$.email.$errors" :key="error.$uid" class="error-msg">
            {{ error.$message }}
          </div>
        </div>

        <div class="label-input" :class="{ error: v$.password.$errors.length }">
          <label for="password"> Password </label> 
          <input
            type="password"
            placeholder="Create Password"
            name="password"
            id="password"
            v-model="state.password"
          />
          <div v-for="error in v$.password.$errors" :key="error.$uid" class="error-msg">
            {{ error.$message }}
          </div>
        </div>

        <div class="label-input" :class="{ error: v$.passwordRepeat.$errors.length }">
          <label for="password-repeat"> Repeat Password </label>
          <input
            type="password"
            placeholder="Re-enter Password"
            name="psw-repeat"
            id="psw-repeat"
            v-model="state.passwordRepeat"
          />
          <div v-for="error in v$.passwordRepeat.$errors" :key="error.$uid" class="error-msg">
            {{ error.$message }}
          </div>
        </div>
        <div class="container signin">
          <p>
            By Creating an account, you agree to Swwipe’s <br>
            <span class="login-texts"> Terms & Conditions </span> and
            <span class="login-texts"> Privacy Policy </span>
          </p>
        </div>

        <button class="btn" type="submit">Create Account</button>

        <p class="buttom">
          Already have a Swwipe account?
          <router-link class="login-router" to="/LoginPage">
            <span class="login-texts">
              Login
              <svg
                width="16"
                height="16"
                viewBox="0 0 16 16"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M3.33302 7.33319L10.7797 7.33319L7.52635 4.07986C7.26635 3.81986 7.26635 3.39319 7.52635 3.13319C7.78635 2.87319 8.20635 2.87319 8.46635 3.13319L12.8597 7.52652C13.1197 7.78652 13.1197 8.20652 12.8597 8.46652L8.47302 12.8665C8.21302 13.1265 7.79302 13.1265 7.53302 12.8665C7.27302 12.6065 7.27302 12.1865 7.53302 11.9265L10.7797 8.66652L3.33302 8.66652C2.96635 8.66652 2.66635 8.36652 2.66635 7.99986C2.66635 7.63319 2.96635 7.33319 3.33302 7.33319Z"
                  fill="#00B6AB"
                /></svg
            ></span>
          </router-link>
        </p>
      </form>
    </section>
  </div>
</template>

<style scoped>


.real-container {
  width: 40%;
  margin: 5% auto;
  background-color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.s-logo {
  border: 3px solid red;
  margin-bottom: 20px;
}

.login-details {
  width: 100%;
  text-align: center;
  color: #4b5563;
}

.label-input {
  width: 100%;
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}



input,
button {
  width: 100%;
  padding: 10px 16px;
  margin: 8px 0;
  box-sizing: border-box;
  border-radius: 5px;
  border: 1px solid #9ea2b3;
  font-weight: 400;
}

button {
  background-color: #00b6ab;
  color: white;
  margin-bottom: 1em;
  cursor: pointer;
}

button:hover {
  background-color: #009688;
}

.Create-texts {
  font-size: 1.2rem;
  font-weight: 800;
  color: #1f2937;
  text-align: left;
}

.header-texts {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 1rem;
  text-align: left;

}

.login-router {
  text-decoration: none;
}

.login-texts {
  color: #00b6ab;
  margin-top: 0.5rem;
}

.error-msg {
  color: red;
  display: flex;
  align-items: center;
  font-size: 0.875rem;
}

.container.signin {
  margin: 1rem 0;
  text-align: left;
}

.buttom {
  font-size: 1rem;
  margin-top: 1rem;
  text-align: left;
}



/* Responsive Design */
@media (max-width: 1200px) {
  .real-container {
    width: 50%;
  }

  .login-texts svg {
    display: flex;
    align-self: center;
  }
}

@media (max-width: 992px) {
  .real-container {
    width: 60%;
  }

  .login-texts svg {
    display: flex;
    align-self: center;
  }
}

@media (max-width: 768px) {
  .real-container {
    width: 80%;
    padding: 1em;
  }
}

@media (max-width: 576px) {
  .real-container {
    width: 90%;
    padding: 1em;
  }

  .Create-texts {
    font-size: 1.2rem;
  }

  .header-texts {
    font-size: 0.9rem;
  }
  .container.signin span {
    display: flex;
    display: inline-block;
  }

  .login-texts {
    font-size: 0.9rem;
    display: flex;
  }
  
  
   .login-texts svg {
    display: flex;
    align-self: center;
  }
}

@media (max-width: 375px) {
  .Create-texts {
    font-size: 1rem;
  }

  .header-texts {
    font-size: 0.8rem;
  }

  .login-texts {
    font-size: 0.8rem;
  }
}
</style>
