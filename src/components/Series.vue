<template>
  <section class="series">
    <h2>Series</h2>
    <ol>
      <li v-for="serie in searchedSeries" :key="serie.id">
        <Card :details="serie"/>
      </li>
    </ol>
  </section>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";

export default {
  name: "Series",
  components: {
    Card,
  },
  props: {
    serie: String,
  },
  data() {
    return {
      searchedSeries: []
    }
  },
  watch: {
    serie(query) {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "6a09bb800f1f7f3929eb20394348e914",
            language: "it-IT",
            query: query,
          },
        })
        .then((response) => {
          this.searchedSeries = response.data.results
        });
    },
  },
};
</script>

<style>
</style>