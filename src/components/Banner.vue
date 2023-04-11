<script>
export default {
  name: 'Banner'
}
</script>

<template>
  <div class="main-banner">
    <h1>Make Your Burguer</h1>
  </div>
</template>



<style scoped>
.main-banner {
  background-image: url('/img/burger.jpg');
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  height: 400px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.main-banner h1 {
  color: #f8f8f8;
  text-align: 60px;
  background-color: #222;
  padding: 20px 40px;

}
</style>