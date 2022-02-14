<template>
  <div id="app">
    <Header />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: { Header },

  mounted() {
    axios.get("https://api.themoviedb.org/3/movie").then(() => {});
  },
};
</script>

<style lang="scss">
</style>
