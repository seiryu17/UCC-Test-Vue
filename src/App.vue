<template>
  <div id="app">
    <div class="container">
      <div class="card mb-3">UCC Test Vehicle</div>
      <VehicleList />
      <notifications group="foo" />
    </div>
  </div>
</template>

<script>
import VehicleList from "./components/VehicleList.vue";

export default {
  name: "App",
  components: {
    VehicleList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
