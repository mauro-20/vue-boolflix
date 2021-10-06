<template>
  <div class="card">
    <img :src="`http://image.tmdb.org/t/p/w342/${details.poster_path}`" :alt="details.title||details.name">
    <h3>Title: {{details.title||details.name}}</h3>
    <h4>Original title: {{details.original_title||details.original_name}}</h4>
    <div>Language: <lang-flag :iso="details.original_language" :squared="false" /></div>
    <div>
      <i v-for="n in fullStars" :key="n" class="fas fa-star"></i>
      <i v-for="n in emptyStars" :key="n" class="far fa-star"></i>
    </div>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: 'Card',
  components: {
    LangFlag
  },
  props: {
    details: Object
  },
  data() {
    return {
      fullStars: null,
      emptyStars: null
    }
  },
  created(){
    this.fullStars = Math.ceil(this.details.vote_average / 2)
    this.emptyStars = 5 - this.fullStars
  }
}
</script>

<style>

</style>