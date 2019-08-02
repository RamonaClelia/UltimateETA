<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <carousel msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import carousel from "./components/carousel.vue";

export default {
  name: "app",
  components: {
    carousel
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  background-color: #eeeeef;
}
.container {
  width: fit-content;
  min-width: 200px;
  margin: 0 auto;
}
</style>
