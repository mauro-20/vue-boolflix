<template>
  <div>
    <h2>Title {{movie.title}}</h2>
    <h3>Original title{{movie.original_title}}</h3>
    <div>Language: {{movie.original_language}}</div>
    <div>vote: {{movie.vote_average}}/10</div>
  </div>
</template>

<script>

export default {
  name: 'Movie',
  methods: {
  },
  props: {
    movie: Object
  }
}
</script>

<style>

</style>