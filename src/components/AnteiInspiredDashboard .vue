<template>
  <div class="flex h-screen bg-black text-white font-sans">
    <!-- Sidebar -->
    <aside class="w-64 bg-black border-r border-green-500 p-6 hidden md:block">
      <h2 class="text-2xl font-bold mb-6 text-green-500">Antei HK</h2>
      <nav>
        <ul class="space-y-2">
          <li v-for="item in sidebarItems" :key="item">
            <a href="#" class="block py-2 px-4 hover:bg-green-500 hover:text-black rounded transition-colors duration-300">
              {{ item }}
            </a>
          </li>
        </ul>
      </nav>
    </aside>

    <!-- Main Content -->
    <div class="flex-1 flex flex-col overflow-hidden">
      <!-- Header -->
      <header class="bg-black border-b border-green-500 p-4 flex justify-between items-center">
        <h1 class="text-2xl font-bold text-green-500">Dashboard</h1>
        <button @click="toggleSidebar" class="md:hidden p-2 rounded-full hover:bg-green-500 hover:text-black transition-colors duration-300">
          <MenuIcon class="h-6 w-6" />
        </button>
      </header>

      <!-- Main Content Area -->
      <main class="flex-1 overflow-x-hidden overflow-y-auto p-6">
        <!-- 9 Horizontal Inputs with 2 Buttons -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
          <div v-for="i in 9" :key="`top-input-${i}`" class="col-span-1 md:col-span-1">
            <input 
              :placeholder="`Input ${i}`"
              class="w-full px-3 py-2 bg-black border border-green-500 rounded-md text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-green-500 transition-colors duration-300"
            >
          </div>
          <div class="col-span-1 md:col-span-3 flex justify-end space-x-4">
            <button class="px-4 py-2 bg-green-500 text-black rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-50 transition-colors duration-300">
              Action 1
            </button>
            <button class="px-4 py-2 bg-black text-green-500 border border-green-500 rounded-md hover:bg-green-500 hover:text-black focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-50 transition-colors duration-300">
              Action 2
            </button>
          </div>
        </div>

        <!-- Tabs -->
        <div class="mb-6">
          <div class="border-b border-green-500">
            <nav class="-mb-px flex space-x-8" aria-label="Tabs">
              <button
                v-for="tab in tabs"
                :key="tab"
                @click="activeTab = tab"
                :class="[
                  activeTab === tab
                    ? 'border-green-500 text-green-500'
                    : 'border-transparent text-gray-500 hover:text-green-500 hover:border-green-500',
                  'whitespace-nowrap py-4 px-1 border-b-2 font-medium text-sm transition-colors duration-300'
                ]"
              >
                {{ tab }}
              </button>
            </nav>
          </div>
        </div>

        <!-- 11 Vertical Inputs -->
        <div class="space-y-4 mb-6">
          <div v-for="i in 11" :key="`bottom-input-${i}`">
            <input 
              :placeholder="`Input ${i}`"
              class="w-full px-3 py-2 bg-black border border-green-500 rounded-md text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-green-500 transition-colors duration-300"
            >
          </div>
        </div>

        <!-- Bottom Buttons -->
        <div class="flex justify-end space-x-4">
          <button class="px-4 py-2 bg-green-500 text-black rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-50 transition-colors duration-300">
            Bottom Action 1
          </button>
          <button class="px-4 py-2 bg-black text-green-500 border border-green-500 rounded-md hover:bg-green-500 hover:text-black focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-50 transition-colors duration-300">
            Bottom Action 2
          </button>
        </div>
      </main>
    </div>

    <!-- Mobile Sidebar -->
    <div v-if="isSidebarOpen" class="fixed inset-0 bg-black bg-opacity-50 z-40 md:hidden" @click="toggleSidebar"></div>
    <aside v-if="isSidebarOpen" class="fixed inset-y-0 left-0 w-64 bg-black border-r border-green-500 p-6 z-50 md:hidden">
      <div class="flex justify-between items-center mb-6">
        <h2 class="text-2xl font-bold text-green-500">Antei HK</h2>
        <button @click="toggleSidebar" class="p-2 rounded-full hover:bg-green-500 hover:text-black transition-colors duration-300">
          <XIcon class="h-6 w-6" />
        </button>
      </div>
      <nav>
        <ul class="space-y-2">
          <li v-for="item in sidebarItems" :key="item">
            <a href="#" class="block py-2 px-4 hover:bg-green-500 hover:text-black rounded transition-colors duration-300">
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
import { MenuIcon, XIcon } from 'lucide-vue-next'

const sidebarItems = ['Dashboard', 'Projects', 'Tasks', 'Reports', 'Settings']
const isSidebarOpen = ref(false)
const activeTab = ref('Tab 1')
const tabs = ['Tab 1', 'Tab 2', 'Tab 3', 'Tab 4']

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
}

/* Добавим неоновый эффект для текста */
.neon-text {
  text-shadow: 0 0 5px #00ff00, 0 0 10px #00ff00, 0 0 15px #00ff00, 0 0 20px #00ff00;
}

/* Добавим неоновый эффект для кнопок */
.neon-button {
  box-shadow: 0 0 5px #00ff00, 0 0 10px #00ff00, 0 0 15px #00ff00, 0 0 20px #00ff00;
}
</style>