<template>
  <main>
    <div>
      <h2>FILMS</h2>
      <ul>
        <li v-for="film in films" :key="film.id">
          <h4>Titolo: {{ film.title }}</h4>
          <p>Titolo originale: {{ film.original_title }}</p>
          <p>Lingua: {{ film.original_language }}</p>
          <p>Voto: {{ film.vote_average }}</p>
        </li>
      </ul>
    </div>

    <div>
      <h2>SERIES</h2>
      <ul>
        <li v-for="serie in series" :key="serie.id">
          <h4>Titolo: {{ serie.name }}</h4>
          <p>Titolo originale: {{ serie.original_name }}</p>
          <p>Lingua: {{ serie.original_language }}</p>
          <p>Voto: {{ serie.vote_average }}</p>
        </li>
      </ul>
    </div>
  </main>
</template>

<script>
export default {
  name: "Cards",
  props: ["films", "series"],
};
</script>

<style>
</style>