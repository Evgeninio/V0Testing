<!-- Сделайте страницу с Сайдбаром, Хедером и блоком с изображениями. Под блоком добавьте две кнопки «Сохранить» и «Удалить». -->
<!-- Ошибка из-за отсутсвующего импорта import { MenuIcon, XIcon } from 'lucide-vue-next' -->
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
        <div class="mb-6">
          <h2 class="text-xl font-semibold mb-4">Image Gallery</h2>
          <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
            <div v-for="i in 8" :key="i" class="bg-purple-700 rounded-lg overflow-hidden">
              <img :src="`/placeholder.svg?height=150&width=150&text=Image ${i}`" :alt="`Image ${i}`" class="w-full h-40 object-cover" />
            </div>
          </div>
        </div>

        <div class="flex space-x-4">
          <button @click="handleSave" class="px-4 py-2 bg-green-500 text-white rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2 focus:ring-offset-purple-900 transition-colors">
            Сохранить
          </button>
          <button @click="handleDelete" class="px-4 py-2 bg-red-500 text-white rounded-md hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2 focus:ring-offset-purple-900 transition-colors">
            Удалить
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

const sidebarItems = ['Dashboard', 'Gallery', 'Settings', 'Profile']
const isSidebarOpen = ref(false)

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value
}

const handleSave = () => {
  console.log('Save button clicked')
  // Здесь можно добавить логику сохранения
  alert('Изменения сохранены')
}

const handleDelete = () => {
  console.log('Delete button clicked')
  // Здесь можно добавить логику удаления
  alert('Элементы удалены')
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
}
</style>