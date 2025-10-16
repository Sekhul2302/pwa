<template>
  <div class="min-h-screen flex items-center justify-center bg-gray-50 dark:bg-gray-900">
    <div class="w-full max-w-sm bg-white dark:bg-gray-800 p-6 rounded-2xl shadow-lg">
      <!-- Logo / Judul -->
      <div class="text-center mb-6">
        <h1 class="text-2xl font-bold text-indigo-600">Welcome Back 👋</h1>
        <p class="text-sm text-gray-500 dark:text-gray-400 mt-1">
          Please sign in to continue
        </p>
      </div>

      <!-- Form -->
      <form @submit.prevent="handleLogin">
        <BaseInput
          label="Email"
          type="email"
          v-model="form.email"
          placeholder="you@example.com"
        />
        <BaseInput
          label="Password"
          type="password"
          v-model="form.password"
          placeholder="••••••••"
        />

        <BaseButton type="submit">Sign In</BaseButton>
      </form>

      <!-- Extra -->
      <p class="text-xs text-gray-400 text-center mt-6">
        Don’t have an account?
        <a href="#" class="text-indigo-600 hover:underline">Sign up</a>
      </p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'
import BaseInput from '@/components/BaseInput.vue'
import BaseButton from '@/components/BaseButton.vue'

const form = reactive({
  email: '',
  password: ''
})

const handleLogin = () => {
  if (!form.email || !form.password) {
    alert('Email dan password harus diisi!')
    return
  }

  // 🔹 Nanti ganti dengan API login kamu
  console.log('Login attempt:', form)
  alert(`Login berhasil untuk ${form.email}`)
}
</script>
