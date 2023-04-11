<script>
import NavBar from './components/NavBar.vue';
import FooterComponent from './components/FooterComponent.vue';
import Logo from '/img/logo.png'

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
  <NavBar :logo="logo" alt="Logotipo" />
  <router-view />
  <FooterComponent />
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
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
