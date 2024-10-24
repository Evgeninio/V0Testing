<!-- Создай страницу c Sidebar слева, Header сверху страницы, далее ниже по горизонтале 9 шт. Input, справа от Input по горизонтале будет 2 шт. 
Button, далее ниже Tabs, далее ниже по вертикале 11 шт. Input, внизу страницы будет 2 шт. Button -->
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
        <!-- 9 Horizontal Inputs with 2 Buttons -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
          <div v-for="i in 9" :key="`top-input-${i}`" class="col-span-1 md:col-span-1">
            <input 
              :placeholder="`Input ${i}`"
              class="w-full px-3 py-2 bg-purple-700 border border-purple-600 rounded-md text-white placeholder-purple-400 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-purple-500"
            >
          </div>
          <div class="col-span-1 md:col-span-3 flex justify-end space-x-4">
            <button class="px-4 py-2 bg-green-500 text-white rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-50 transition-colors">
              Action 1
            </button>
            <button class="px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-opacity-50 transition-colors">
              Action 2
            </button>
          </div>
        </div>

        <!-- Tabs -->
        <div class="mb-6">
          <div class="border-b border-purple-700">
            <nav class="-mb-px flex space-x-8" aria-label="Tabs">
              <button
                v-for="tab in tabs"
                :key="tab"
                @click="activeTab = tab"
                :class="[
                  activeTab === tab
                    ? 'border-purple-500 text-purple-300'
                    : 'border-transparent text-purple-400 hover:text-purple-300 hover:border-purple-300',
                  'whitespace-nowrap py-4 px-1 border-b-2 font-medium text-sm'
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
              class="w-full px-3 py-2 bg-purple-700 border border-purple-600 rounded-md text-white placeholder-purple-400 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-purple-500"
            >
          </div>
        </div>

        <!-- Bottom Buttons -->
        <div class="flex justify-end space-x-4">
          <button class="px-4 py-2 bg-yellow-500 text-white rounded-md hover:bg-yellow-600 focus:outline-none focus:ring-2 focus:ring-yellow-500 focus:ring-opacity-50 transition-colors">
            Bottom Action 1
          </button>
          <button class="px-4 py-2 bg-red-500 text-white rounded-md hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-opacity-50 transition-colors">
            Bottom Action 2
          </button>
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
</style>