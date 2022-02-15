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
          <p>Voto: {{ item.vote_average }}</p>
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
    };
  },

  computed: {
    flag() {
      return require(`@/assets/img/${this.item.original_language}.png`);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>