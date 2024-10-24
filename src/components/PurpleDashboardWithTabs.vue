<!-- Создайте страницу с Сайдбаром и Хедером. 
Под Хедером добавьте два таба, в первом табе — список с чекбоксами, во втором — форму с четырьмя полями ввода и двумя кнопками под ними. -->
<!-- import { MenuIcon, XIcon } from 'lucide-vue-next' -->
<template>
  <div class="flex h-screen bg-purple-900 text-white">
    <!-- Sidebar -->
    <aside class="w-64 bg-purple-800 p-6 hidden md:block">
      <h2 class="text-2xl font-bold mb-6">Sidebar</h2>
      <nav>
        <ul class="space-y-2">
          <li v-for="item in sidebarItems" :key="item">
            <a href="#" class="block py-2 px-4 hover:bg-purple-700 rounded transition-colors">
              {{ item }}
            </a>
          </li>
        </ul>
      </nav>
    </aside>

    <!-- Main Content -->
    <div class="flex-1 flex flex-col overflow-hidden">
      <!-- Header -->
      <header class="bg-purple-800 p-4 flex justify-between items-center">
        <h1 class="text-2xl font-bold">Dashboard</h1>
        <button @click="toggleSidebar" class="md:hidden p-2 rounded-full hover:bg-purple-700 transition-colors">
          <MenuIcon class="h-6 w-6" />
        </button>
      </header>

      <!-- Main Content Area -->
      <main class="flex-1 overflow-x-hidden overflow-y-auto p-6">
        <!-- Tabs -->
        <div class="mb-4">
          <button 
            v-for="(tab, index) in tabs" 
            :key="tab"
            @click="activeTab = index"
            class="px-4 py-2 mr-2 rounded-t-lg font-medium transition-colors"
            :class="activeTab === index ? 'bg-purple-700 text-white' : 'bg-purple-800 text-purple-300 hover:bg-purple-700'"
          >
            {{ tab }}
          </button>
        </div>

        <!-- Tab Content -->
        <div class="bg-purple-800 rounded-lg p-6">
          <!-- Checklist Tab -->
          <div v-if="activeTab === 0">
            <h3 class="text-xl font-semibold mb-4">Checklist</h3>
            <ul class="space-y-2">
              <li v-for="(item, index) in checklistItems" :key="index" class="flex items-center">
                <input 
                  :id="'checkbox-' + index"
                  v-model="item.checked"
                  type="checkbox"
                  class="form-checkbox h-5 w-5 text-green-500 rounded border-purple-500 focus:ring-green-500 focus:ring-opacity-50"
                >
                <label :for="'checkbox-' + index" class="ml-2 text-purple-200">{{ item.text }}</label>
              </li>
            </ul>
          </div>

          <!-- Form Tab -->
          <div v-else-if="activeTab === 1">
            <h3 class="text-xl font-semibold mb-4">Form</h3>
            <form @submit.prevent="handleSubmit" class="space-y-4">
              <div v-for="(field, index) in formFields" :key="index">
                <label :for="field.id" class="block text-sm font-medium text-purple-300 mb-1">{{ field.label }}</label>
                <input 
                  :id="field.id"
                  v-model="field.value"
                  :type="field.type"
                  :placeholder="field.placeholder"
                  class="w-full px-3 py-2 bg-purple-700 border border-purple-600 rounded-md text-white placeholder-purple-400 focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-green-500"
                >
              </div>
              <div class="flex space-x-4">
                <button type="submit" class="px-4 py-2 bg-green-500 text-white rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-50 transition-colors">
                  Submit
                </button>
                <button type="button" @click="resetForm" class="px-4 py-2 bg-purple-600 text-white rounded-md hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-opacity-50 transition-colors">
                  Reset
                </button>
              </div>
            </form>
          </div>
        </div>
      </main>
    </div>

    <!-- Mobile Sidebar -->
    <div v-if="isSidebarOpen" class="fixed inset-0 bg-black bg-opacity-50 z-40 md:hidden" @click="toggleSidebar"></div>
    <aside v-if="isSidebarOpen" class="fixed inset-y-0 left-0 w-64 bg-purple-800 p-6 z-50 md:hidden">
      <div class="flex justify-between items-center mb-6">
        <h2 class="text-2xl font-bold">Sidebar</h2>
        <button @click="toggleSidebar" class="p-2 rounded-full hover:bg-purple-700 transition-colors">
          <XIcon class="h-6 w-6" />
        </button>
      </div>
      <nav>
        <ul class="space-y-2">
          <li v-for="item in sidebarItems" :key="item">
            <a href="#" class="block py-2 px-4 hover:bg-purple-700 rounded transition-colors">
              {{ item }}
            </a>
          </li>
        </ul>
      </nav>
    </aside>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const sidebarItems = ['Dashboard', 'Projects', 'Tasks', 'Settings']
const isSidebarOpen = ref(false)
const activeTab = ref(0)
const tabs = ['Checklist', 'Form']

const checklistItems = ref([
  { text: 'Complete project proposal', checked: false },
  { text: 'Review team performance', checked: false },
  { text: 'Update client documentation', checked: false },
  { text: 'Schedule team meeting', checked: false },
])

const formFields = ref([
  { id: 'name', label: 'Name', type: 'text', placeholder: 'Enter your name', value: '' },
  { id: 'email', label: 'Email', type: 'email', placeholder: 'Enter your email', value: '' },
  { id: 'phone', label: 'Phone', type: 'tel', placeholder: 'Enter your phone number', value: '' },
  { id: 'message', label: 'Message', type: 'text', placeholder: 'Enter your message', value: '' },
])

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value
}

const handleSubmit = () => {
  console.log('Form submitted:', formFields.value.map(field => ({ [field.id]: field.value })))
  // Здесь можно добавить логику отправки формы
  alert('Form submitted successfully!')
}

const resetForm = () => {
  formFields.value.forEach(field => field.value = '')
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
}
</style>