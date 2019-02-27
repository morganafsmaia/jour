<template>
  <div id="app">
    <h1>Jour</h1>
    <app-time></app-time>
    <app-weather></app-weather>
  </div>
</template>

<script>
//importing the components
import Weather from "./components/weather.vue";
import Time from "./components/time.vue";

export default {
  name: "app",
  components: {
    "app-weather": Weather,
    "app-time": Time
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
}
</style>
