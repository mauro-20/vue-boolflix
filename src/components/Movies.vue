<template>
  <section>
    <ol>
      <li v-for="(movie, index) in searchedMovies" :key="index">
        <Movie :movie="movie"/>
      </li>
    </ol>
  </section>
</template>

<script>
import axios from "axios";
import Movie from "./Movie.vue";

export default {
  name: "Movies",
  components: {
    Movie,
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
    movie(value) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "6a09bb800f1f7f3929eb20394348e914",
            language: "it-IT",
            query: value,
          },
        })
        .then((response) => {
          this.searchedMovies = response.data.results
        });
    },
  },
};
</script>

<style>
</style>