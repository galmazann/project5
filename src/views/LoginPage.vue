<template>
  <form class="max-w-md mx-auto p-8 bg-white rounded-lg shadow-md" @submit.prevent>
    <h2 class="text-2xl font-bold mb-6 text-center text-gray-800">Login</h2>
    
    <div class="mb-4">
      <label for="username" class="block mb-2 font-semibold text-gray-700">Username</label>
      <input
        id="username"
        v-model="username"
        type="text"
        placeholder="Enter your username"
        class="w-full p-3 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-green-300 transition duration-200"
      />
    </div>
    
    <div class="mb-6">
      <label for="password" class="block mb-2 font-semibold text-gray-700">Password</label>
      <input
        id="password"
        v-model="password"
        type="password"
        placeholder="Enter your password"
        class="w-full p-3 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-green-300 transition duration-200"
      />
    </div>
    
    <button 
      @click="logUserIn" 
      class="w-full bg-green-500 text-white py-2 rounded-md hover:bg-green-700 transition duration-200"
    >
      LOGIN
    </button>
  </form>
</template>

<script setup>
import { ref } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import { useAuth } from '../composables/useAuth'

const { login, logout } = useAuth()

const router = useRouter()
const route = useRoute()

const username = ref('')
const password = ref('')

const logUserIn = async () => {
  if (await login(username.value, password.value)) {
    if (route.query.redirect) {
      router.push(route.query.redirect)
    } else {
      router.push({ name: 'SettingsPage' })
    }
  } else {
    logout()
  }
}
</script>

<style scoped>

</style>
