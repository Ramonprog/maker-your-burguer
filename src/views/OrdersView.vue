<script>
import DashboardVue from '../components/Dashboard.vue';
export default {
  name: 'OrdersView',
  components: {
    DashboardVue,
    data() {
      return {
        burgers: null,
        burgers_id: null,
        status: []
      }
    }
  }
}
</script>

<template>
  <div class="main-container">
    <h1>Gerenciar pedidos:</h1>
    <DashboardVue />
  </div>
</template>

<style></style>
