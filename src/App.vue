<template>
  <div id="app">
    <Header @search="queryToSearch"/>
    <main>
      <div class="container">
        <Movies :movie="query"/>
        <Series :serie="query"/>
      </div>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Movies from './components/Movies.vue'
import Series from './components/Series.vue'

export default {
  name: 'App',
  components: {
    Header,
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
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta2/css/all.min.css");
@import './assets/style/common';

  

</style>
