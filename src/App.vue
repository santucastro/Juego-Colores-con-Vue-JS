<template>
  <div id="app">
    <Juego />
  </div>
</template>

<script>
/* import HelloWorld from './components/HelloWorld.vue' */
import Juego from "./components/Juego.vue";

export default {
  name: "App",
  components: {
    Juego
  },
};
</script>

<style>
#app {
/*   font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center; */
  color: #2c3e50;
  /*   margin-top: 60px; */
}
body {
  background: #232323;
  margin: 0;
  font-family: "Montserrat", "Avenir";
}
</style>
