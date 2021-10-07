<template>
  <section v-if="searchedMovies" class="movies">
    <h2>MOVIES</h2>
    <div class="main-section-container" >
      <button class="btn-scroll left" @click="prev"><i class="fas fa-angle-left"></i></button>
      <div class="scroll-container" ref="scrollContainer">
        <div v-for="movie in searchedMovies" :key="movie.id">
          <Card :details="movie"/>
        </div>
      </div>
      <button class="btn-scroll right" @click="next"><i class="fas fa-angle-right"></i></button>
    </div>
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
      searchedMovies: null
    }
  },
  methods: {
    next: function() {
      this.$refs.scrollContainer.scrollLeft += 500
    },
    prev: function() {
      this.$refs.scrollContainer.scrollLeft -= 500
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

<style lang="scss" scoped>
  @import '../assets/style/mainSections';
  
  .movies{
    margin-bottom: 1.875rem;
  }

  .main-section-container{
    position: relative;

    .btn-scroll{
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      z-index: 1;
      
      &.left{
        left: .625rem;
      }
      &.right{
        left: 93%;
      }
    }
  }

  ::-webkit-scrollbar {
    display: none;
  }

</style>