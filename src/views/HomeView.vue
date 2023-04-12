<script>
import BannerVue from "../components/Banner.vue";
import BurgerFormVue from '../components/BurgerForm.vue';

export default {
  name: 'Home',
  components: {
    BannerVue,
    BurgerFormVue
  }
}
</script>

<template>
  <BannerVue />
  <main class="main-container">
    <h1>Monte o seu Burger:</h1>
    <BurgerFormVue />
  </main>
</template>
