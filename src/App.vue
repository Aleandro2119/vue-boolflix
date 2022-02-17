<template>
  <div>
    <Header @search="search" />
    <section>
      <h2 class="text-center text-white">FILMS</h2>
      <Main v-for="film in films" :key="film.id" :item="film" />
    </section>
    <section>
      <h2 class="text-center text-white">SERIES</h2>
      <Main v-for="serie in series" :key="serie.id" :item="serie" />
    </section>
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
      series: [],
      api: {
        language: "it-IT",
        api_key: "c98fc689e4d66d8a1762d048d057e91b",
        url: "https://api.themoviedb.org/3",
      },
    };
  },

  methods: {
    search(query) {
      if (!query) {
        this.films = [];
        this.series = [];
        return;
      }

      const { api_key, language } = this.api;
      const config = {
        params: {
          api_key: api_key,
          query: query,
          language,
        },
      };

      this.fetchApi("search/movie", config, "films");
      this.fetchApi("search/tv", config, "series");
    },

    fetchApi(endpoint, config, target) {
      axios.get(`${this.api.url}/${endpoint}`, config).then((res) => {
        this[target] = res.data.results;
      });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
body {
  background-color: #434343;
}
</style>
