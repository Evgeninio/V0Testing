<script>
  import PurpleDashboard from './components/PurpleDashboard.vue';
  import  PurpleFormPage from '../src/components/PurpleFormPage.vue'
  import PurpleDashboardWithCards from './components/PurpleDashboardWithCards.vue';
  import PurpleDashboardWithTabs from './components/PurpleDashboardWithTabs.vue';
  import ComplexDashboardLayout from './components/ComplexDashboardLayout.vue';
  import AnteiInspiredDashboard from './components/AnteiInspiredDashboard.vue';
  export default {
    components: {
      PurpleFormPage,
      PurpleDashboard,
      PurpleDashboardWithCards,
      PurpleDashboardWithTabs,
      ComplexDashboardLayout,
      AnteiInspiredDashboard
    }
  }
</script>

<template>
  <PurpleDashboardWithCards />
</template>

<style scoped>

</style>
