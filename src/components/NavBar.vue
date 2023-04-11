<script >
export default {
  name: 'NavBar',
  props: ['logo', 'alt']
}
</script>

<template>
  <nav>
    <div class="logo">
      <RouterLink to="/">
        <img :src="logo" :alt="alt" id="logo">
      </RouterLink>
    </div>
    <div class="links">
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/pedidos">About</RouterLink>
    </div>

  </nav>
</template>



<style scoped>
nav {
  background-color: #222;
  border-bottom: 4px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav .logo img {
  width: 40px;
  height: 40px;
}

nav a {
  color: #fcba03;
  text-decoration: none;
  margin: 12px;
  transition: .2s;
}

nav a:hover {
  color: #fff;
}
</style>