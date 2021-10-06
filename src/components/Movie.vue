<template>
  <div>
    <h2>Title {{movie.title}}</h2>
    <h3>Original title{{movie.original_title}}</h3>
    <div>Language: <lang-flag :iso="movie.original_language" :squared="false"/></div>
    <div>vote: {{movie.vote_average}}/10</div>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: 'Movie',
  components: {
    LangFlag
  },
  methods: {
  },
  props: {
    movie: Object
  }
}
</script>

<style>

</style>