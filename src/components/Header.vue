<template>
  <header class="d-flex justify-content-between align-items-center p-3">
    <h1>BOOLFLIX</h1>
    <div id="searc">
      <input v-model.trim="query" type="text" /><button
        type="button"
        @click="getSearch"
      >
        Cerca
      </button>
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


<style lang="scss" scoped>
header {
  background-color: #000000;

  h1 {
    color: red;
  }
}
</style>