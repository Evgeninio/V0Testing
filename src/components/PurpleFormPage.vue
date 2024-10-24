<template>
  <div class="min-h-screen bg-purple-900 text-white p-6">
    <header class="mb-8">
      <h1 class="text-3xl font-bold">Company Form</h1>
    </header>

    <form @submit.prevent="handleSubmit" class="max-w-2xl mx-auto bg-purple-800 p-6 rounded-lg shadow-lg">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
        <div>
          <label for="firstName" class="block text-sm font-medium mb-1">First Name</label>
          <input
            id="firstName"
            v-model="form.firstName"
            type="text"
            class="w-full px-3 py-2 bg-purple-700 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500"
            required
          >
        </div>
        <div>
          <label for="lastName" class="block text-sm font-medium mb-1">Last Name</label>
          <input
            id="lastName"
            v-model="form.lastName"
            type="text"
            class="w-full px-3 py-2 bg-purple-700 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500"
            required
          >
        </div>
        <div>
          <label for="email" class="block text-sm font-medium mb-1">Email</label>
          <input
            id="email"
            v-model="form.email"
            type="email"
            class="w-full px-3 py-2 bg-purple-700 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500"
            required
          >
        </div>
        <div>
          <label for="phone" class="block text-sm font-medium mb-1">Phone</label>
          <input
            id="phone"
            v-model="form.phone"
            type="tel"
            class="w-full px-3 py-2 bg-purple-700 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500"
            required
          >
        </div>
      </div>

      <div class="flex justify-between">
        <button
          type="submit"
          class="px-4 py-2 bg-green-500 text-white rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2 focus:ring-offset-purple-800"
        >
          Сохранить
        </button>
        <button
          type="button"
          @click="handleCancel"
          class="px-4 py-2 bg-gray-500 text-white rounded-md hover:bg-gray-600 focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-offset-2 focus:ring-offset-purple-800"
        >
          Отменить
        </button>
        <button
          type="button"
          @click="handleClear"
          class="px-4 py-2 bg-red-500 text-white rounded-md hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2 focus:ring-offset-purple-800"
        >
          Очистить
        </button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { reactive } from 'vue'

const form = reactive({
  firstName: '',
  lastName: '',
  email: '',
  phone: ''
})

const handleSubmit = () => {
  // Here you would typically send the form data to a server
  console.log('Form submitted:', form)
  alert('Form submitted successfully!')
}

const handleCancel = () => {
  // Here you might want to navigate away or close a modal
  console.log('Form cancelled')
  alert('Form cancelled')
}

const handleClear = () => {
  form.firstName = ''
  form.lastName = ''
  form.email = ''
  form.phone = ''
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
}
</style>