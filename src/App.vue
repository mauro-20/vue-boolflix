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
