<template>
  <div id="app">
    <Header @search="queryToSearch"/>
    <main>
      <div class="container">
        <Collection :title="'MOVIES'" :movie="query" :genres="genreList"/>
        <Collection :title="'SERIES'" :serie="query" :genres="genreList"/>
        <Collection :title="'TRENDING MOVIES'" :trendMovies="trendingMovies" :genres="genreList"/>
        <Collection :title="'TRENDING SERIES'" :trendSeries="trendingSeries" :genres="genreList"/>
        
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Header from './components/Header.vue'
import Collection from './components/Collection.vue'

export default {
  name: 'App',
  components: {
    Header,
    Collection
  },
  data() {
    return {
      query: "",
      trendingMovies: false,
      trendingSeries: false,
      genreList: null
    }
  },
  methods: {
    queryToSearch(query) {
      this.query = query
    }
  },
  created() {
    this.trendingMovies = true;
    this.trendingSeries = true;
    // call api genres list
    axios
      .get("https://api.themoviedb.org/3/genre/movie/list", {
        params: {
          api_key: "6a09bb800f1f7f3929eb20394348e914",
          language: "it-IT"
        },
      })
      .then((response) => {
        this.genreList = response.data.genres;
      }); 
  }
}
</script>

<style lang="scss">
  @import '~@fortawesome/fontawesome-free/css/all.css';
  @import './assets/style/common';

  /* scrollbar */
  ::-webkit-scrollbar {
    width: 10px;
  }
  ::-webkit-scrollbar-track {
    background-color: rgba(50, 50, 50, 0.5);
  }
  ::-webkit-scrollbar-thumb {
    background: #6d6d6d; 
    border-radius: 5px;
  }
  ::-webkit-scrollbar-thumb:hover {
    background: #c1c1c1c1; 
  }  

</style>
