<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <carousel msg="Welcome to Your Vue.js App" />
    <catcont />
  </div>
</template>

<script>
import carousel from "./components/carousel.vue";
import catcont from "./components/catcont.vue";


export default {
  name: "app",
  components: {
    carousel,
    catcont
  }
};
</script>

<style>
body {
  background-color: whitesmoke;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  /* background-color: #eeeeef; */
}
.container {
  width: fit-content;
  min-width: 200px;
  margin: 0 auto;
}
</style>
