<template>
  <div class="card">
    <h3>Title: {{details.title||details.name}}</h3>
    <h4>Original title: {{details.original_title||details.original_name}}</h4>
    <div>Language: <lang-flag :iso="details.original_language" :squared="false" /></div>
    <div>vote: {{details.vote_average}}/10</div>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: 'Card',
  components: {
    LangFlag
  },
  methods: {
  },
  props: {
    details: Object
  }
}
</script>

<style>

</style>