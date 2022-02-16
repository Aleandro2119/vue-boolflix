<template>
  <main>
    <div>
      <ul>
        <li>
          <h4>Titolo: {{ item.title || item.name }}</h4>
          <p>
            Titolo originale: {{ item.original_title || item.original_name }}
          </p>
          <img
            v-if="countries.includes(item.original_language)"
            :src="flag"
            alt=""
          />
          <p v-else>Lingua: {{ item.original_language }}</p>
          <div>
            Voto:
            <i
              v-for="n in 5"
              :key="n"
              class="fa-star"
              :class="n <= vote ? 'far' : 'fas'"
            ></i>
          </div>
          <img :src="poster" :alt="title" />
        </li>
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
</style>