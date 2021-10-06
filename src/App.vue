<template>
  <div id="app">
    <Search-Bar @search="queryToSearch"/>
    <Movies :movie="query"/>
    <Series :serie="query"/>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import Movies from './components/Movies.vue'
import Series from './components/Series.vue'

export default {
  name: 'App',
  components: {
    SearchBar,
    Movies,
    Series
  },
  data() {
    return {
      query: ""
    }
  },
  methods: {
    queryToSearch(query) {
      this.query = query
    }
  }
}
</script>

<style lang="scss">


</style>
