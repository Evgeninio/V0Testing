<!-- Сделайте страницу с Сайдбаром, Хедером и горизонтальной кнопкой «Добавить» под ним. 
Ниже разместите карточки данных в три столбца с кнопками действий на каждой карточке. -->
<!-- Ошибка импорта import { MenuIcon, XIcon, PlusIcon, EditIcon, TrashIcon } from 'lucide-vue-next' -->
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
        <!-- Add Button -->
        <div class="mb-6">
          <button @click="handleAdd" class="w-full bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded transition-colors">
            <PlusIcon class="inline-block mr-2 h-5 w-5" />
            Добавить
          </button>
        </div>

        <!-- Cards Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div v-for="card in cards" :key="card.id" class="bg-purple-800 rounded-lg shadow-lg p-6">
            <h3 class="text-xl font-semibold mb-2">{{ card.title }}</h3>
            <p class="text-purple-200 mb-4">{{ card.description }}</p>
            <div class="flex justify-end space-x-2">
              <button @click="handleEdit(card.id)" class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded transition-colors">
                <EditIcon class="h-4 w-4" />
              </button>
              <button @click="handleDelete(card.id)" class="bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded transition-colors">
                <TrashIcon class="h-4 w-4" />
              </button>
            </div>
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
import { MenuIcon, XIcon, PlusIcon, EditIcon, TrashIcon } from 'lucide-vue-next'

const sidebarItems = ['Dashboard', 'Projects', 'Tasks', 'Settings']
const isSidebarOpen = ref(false)

const cards = ref([
  { id: 1, title: 'Project Alpha', description: 'A groundbreaking initiative for innovation.' },
  { id: 2, title: 'Task Beta', description: 'Crucial task for project success.' },
  { id: 3, title: 'Initiative Gamma', description: 'Exploring new frontiers in technology.' },
  { id: 4, title: 'Operation Delta', description: 'Streamlining our core processes.' },
  { id: 5, title: 'Venture Epsilon', description: 'Expanding into new markets.' },
  { id: 6, title: 'Program Zeta', description: 'Training and development initiative.' },
])

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value
}

const handleAdd = () => {
  console.log('Add button clicked')
  // Здесь можно добавить логику для добавления новой карточки
  alert('Добавление новой карточки')
}

const handleEdit = (id) => {
  console.log('Edit button clicked for card', id)
  // Здесь можно добавить логику для редактирования карточки
  alert(`Редактирование карточки ${id}`)
}

const handleDelete = (id) => {
  console.log('Delete button clicked for card', id)
  // Здесь можно добавить логику для удаления карточки
  alert(`Удаление карточки ${id}`)
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
}
</style>