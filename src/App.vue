<template>
  <div id="app">
    <Header @search="searchElement" />
    <Main :films="films" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },

  data() {
    return {
      films: [],
      api: {
        language: "it-IT",
        api_key: "c98fc689e4d66d8a1762d048d057e91b",
        url: "https://api.themoviedb.org/3",
      },
    };
  },

  methods: {
    searchElement(query) {
      const { api_key, url, language } = this.api;

      const config = {
        params: {
          api_key: api_key,
          query: query,
          language,
        },
      };

      axios.get(`${url}/search/movie`, config).then((res) => {
        this.films = res.data.results;
      });
    },
  },
};
</script>

<style lang="scss">
</style>
