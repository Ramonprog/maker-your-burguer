<script>
import NavBar from './components/NavBar.vue';
import FooterComponent from './components/FooterComponent.vue';
import Logo from '/img/logo.png'
import { toast } from 'vue3-toastify';

export default {
  name: 'App',
  components: {
    NavBar,
    FooterComponent
  },
  data() {
    return {
      logo: Logo
    }
  }
}
</script>

<template>
  <div class="app">
    <NavBar :logo="logo" alt="Logotipo" />
    <router-view />
    <FooterComponent />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
  list-style: none;
}

.app {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>
