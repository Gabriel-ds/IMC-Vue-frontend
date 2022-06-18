<template>
  <h1 class="center">Calcule o seu IMC</h1>
  <AddImc />
</template>

<script>
import AddImc from "./components/AddImc.vue";
export default {
  name: "App",
  components: {
    AddImc,
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
