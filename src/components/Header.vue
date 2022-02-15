<template>
  <header>
    <div>
      <div>
        <input v-model.trim="query" type="text" /><button
          type="button"
          @click="getSearch"
        >
          Cerca
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",

  data() {
    return {
      query: "",
    };
  },
  methods: {
    getSearch() {
      this.$emit("search", this.query);
    },
  },
};
</script>

<style>
</style>