<template>
  <section v-if="searchedSeries" class="series">
    <h2>SERIES</h2>
    <div class="main-section-container" >
      <button class="btn-scroll left" @click="prev"><i class="fas fa-angle-left"></i></button>
      <div class="scroll-container" ref="scrollContainer">
        <div v-for="serie in searchedSeries" :key="serie.id">
          <Card :details="serie"/>
        </div>
      </div>
      <button class="btn-scroll right" @click="next"><i class="fas fa-angle-right"></i></button>
    </div>
  </section>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";

export default {
  name: "Series",
  components: {
    Card,
  },
  props: {
    serie: String,
  },
  data() {
    return {
      searchedSeries: null
    }
  },
  methods: {
    next: function() {
      this.$refs.scrollContainer.scrollLeft += 500
    },
    prev: function() {
      this.$refs.scrollContainer.scrollLeft -= 500
    }
  },
  watch: {
    serie(query) {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "6a09bb800f1f7f3929eb20394348e914",
            language: "it-IT",
            query: query,
          },
        })
        .then((response) => {
            this.searchedSeries = response.data.results
        });
    },
  },
};
</script>

<style lang="scss" scoped>
  @import '../assets/style/mainSections';
  
  .series{
    margin-bottom: 1.875rem;
  }

  .main-section-container{
    position: relative;

    .btn-scroll{
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      z-index: 1;
      
      &.left{
        left: .625rem;
      }
      &.right{
        left: 93%;
      }
    }
  }

  ::-webkit-scrollbar {
    display: none;
  }

</style>