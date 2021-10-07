<template>
  <header>
    <div class="logo">BOOLFLIX</div>
    <form>
      <input type="text" name="search" id="search" class="input-text" placeholder="Begin your search" v-model="searchInput">
      <button type="submit" class="btn" @click.prevent="$emit('search', searchInput)">Search</button>
    </form>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      searchInput: ''
    }
  }
}
</script>

<style lang="scss" scoped>
  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.25rem 2.5rem 1.25rem 2.5rem;
    background-color: #000;

    .logo{
      font-size: 2.5rem;
      font-weight: 900;
      color: #e10712;
    }

    form{
      display: flex;
      align-items: center;
    }

  }

</style>