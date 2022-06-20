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

