<template>
  <header>
    <h1>BOOLFLIX</h1>
    <input v-model.trim="query" type="text" /><button
      type="button"
      @click="getSearch"
    >
      Cerca
    </button>
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

<style lang="scss" scoped>
header {
  background-color: #000000;
  height: 80px;
  display: flex;
  align-items: center;

  h1 {
    color: red;
  }
}
</style>