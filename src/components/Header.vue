<template>
  <header>
    <div>
      <div>
        <input v-model="search" type="text" /><button type="button">
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
      search: "",
    };
  },
};
</script>

<style>
</style>