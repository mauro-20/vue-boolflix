<template>
  <div id="app">
    <Header @search="queryToSearch"/>
    <main>
      <div class="container">
        <Collection :title="'MOVIES'" :movie="query"/>
        <Collection :title="'SERIES'" :serie="query"/>
      </div>
    </main>
  </div>
</template>

<script>
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
