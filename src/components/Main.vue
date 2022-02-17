<template>
  <main>
    <div class="d-flex justify-content-center align-items-center">
      <ul>
        <li>
          <h4 class="text-white">Titolo: {{ item.title || item.name }}</h4>
          <p class="mt-4 text-white">
            Titolo originale: {{ item.original_title || item.original_name }}
          </p>
          <img
            class="flags"
            v-if="countries.includes(item.original_language)"
            :src="flag"
            alt=""
          />
          <p class="mt-4 text-white" v-else>
            Lingua: {{ item.original_language }}
          </p>
          <div class="mt-4 text-white">
            Voto:
            <i
              v-for="n in 5"
              :key="n"
              class="fa-star"
              :class="n <= vote ? 'fa-solid' : 'fa-regular'"
            ></i>
          </div>
        </li>
        <img :src="poster" :alt="title" class="img-fluid" />
      </ul>
    </div>
  </main>
</template>

<script>
export default {
  name: "Cards",
  props: ["item"],

  data() {
    return {
      countries: ["it", "en"],
      img: {
        url: "https://image.tmdb.org/t/p/w342",
        placeholder:
          "https://www.altavod.com/assets/images/poster-placeholder.png",
      },
    };
  },

  computed: {
    flag() {
      return require(`@/assets/img/${this.item.original_language}.png`);
    },

    title() {
      return this.item.title || this.item.name;
    },

    poster() {
      if (!this.item.poster_path) return this.img.placeholder;
      return this.img.url + this.item.poster_path;
    },

    vote() {
      return Math.ceil(this.item.vote_average / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
.flags {
  width: 25%;
  margin-top: 40px;
}

ul {
  height: auto;
  width: 342px;
  border: 1px solid white;
  overflow-y: scroll;
  padding-left: 0;
}

li {
  display: none;
  font-size: 14px;
  text-align: center;
}

ul:hover li {
  display: inline;
  position: absolute;
  background-color: black;
  width: 341px;
  height: 487px;
  border: 1px solid white;
  padding-left: 0;
}

.fa-star {
  color: gray;
}
</style>