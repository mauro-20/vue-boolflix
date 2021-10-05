<template>
  <div id="app">
    <Search-Bar @search="movieToSearch"/>
    <Movies :movie="movie"/>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import Movies from './components/Movies.vue'

export default {
  name: 'App',
  components: {
    SearchBar,
    Movies
  },
  data() {
    return {
      movie: ""
    }
  },
  methods: {
    movieToSearch(movie) {
      console.log(movie)
      this.movie = movie
    }
  }
}
</script>

<style lang="scss">


</style>
