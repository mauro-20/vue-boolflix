<template>
  <div>
    <input type="text" name="search" id="search" v-model="searchInput">
    <button @click="$emit('search', searchInput)">Search</button>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  data() {
    return {
      searchInput: ''
    }
  }
}
</script>

<style>

</style>