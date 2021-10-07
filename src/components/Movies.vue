<template>
  <section v-if="movie" class="movies">
    <h2>Movies</h2>
    <ul class="main-section-container">
      <li v-for="movie in searchedMovies" :key="movie.id">
        <Card :details="movie"/>
      </li>
    </ul>
  </section>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";

export default {
  name: "Movies",
  components: {
    Card,
  },
  props: {
    movie: String,
  },
  data() {
    return {
      searchedMovies: []
    }
  },
  watch: {
    movie(query) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "6a09bb800f1f7f3929eb20394348e914",
            language: "it-IT",
            query: query,
          },
        })
        .then((response) => {
          this.searchedMovies = response.data.results
        });
    },
  },
};
</script>

<style lang>

  

</style>