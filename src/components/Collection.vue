<template>
  <section v-if="searchedMovies" class="movies">
    <h2>{{ title }}</h2>
    <div class="main-section-container">
      <button class="btn-scroll left" @click="prev">
        <i class="fas fa-angle-left"></i>
      </button>
      <div class="scroll-container" ref="scrollContainer">
        <div v-for="movie in searchedMovies" :key="movie.id">
          <Card :details="movie" />
        </div>
      </div>
      <button class="btn-scroll right" @click="next">
        <i class="fas fa-angle-right"></i>
      </button>
    </div>
  </section>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";

export default {
  name: "Collection",
  components: {
    Card,
  },
  props: {
    title: String,
    movie: String,
    serie: String,
    trendSeries: Boolean,
    trendMovies: Boolean,
  },
  data() {
    return {
      searchedMovies: null,
      api_key: "6a09bb800f1f7f3929eb20394348e914",
      language: "it-IT",
    };
  },
  methods: {
    next: function () {
      let scroll = this.$refs.scrollContainer.scrollLeft + 1000;
      this.$refs.scrollContainer.scroll({
        left: scroll,
        top: 0,
        behavior: "smooth",
      });
    },
    prev: function () {
      let scroll = this.$refs.scrollContainer.scrollLeft - 1000;
      this.$refs.scrollContainer.scroll({
        left: scroll,
        top: 0,
        behavior: "smooth",
      });
    },
  },
  watch: {
    movie(query) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: this.api_key,
            language: this.language,
            query: query,
          },
        })
        .then((response) => {
          this.searchedMovies = response.data.results;
        });
    },
    serie(query) {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: this.api_key,
            language: this.language,
            query: query,
          },
        })
        .then((response) => {
          this.searchedMovies = response.data.results;
        });
    },
  },
  created() {
    if (this.trendMovies) {
      axios
        .get("https://api.themoviedb.org/3/trending/movie/week", {
          params: {
            api_key: this.api_key,
            language: this.language
          },
        })
        .then((response) => {
          this.searchedMovies = response.data.results;
        });
    }
    if (this.trendSeries) {
      axios
        .get("https://api.themoviedb.org/3/trending/tv/week", {
          params: {
            api_key: this.api_key,
            language: this.language
          },
        })
        .then((response) => {
          this.searchedMovies = response.data.results;
        });
    }
  },
};
</script>

<style lang="scss" scoped>
h2 {
  margin: 1.25rem 0;
}
.movies {
  margin-bottom: 1.875rem;
}

.main-section-container {
  display: flex;
  overflow-x: auto;
  position: relative;

  .btn-scroll {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    z-index: 1;

    &.left {
      left: 0.625rem;
    }
    &.right {
      left: 93%;
    }
  }
  .scroll-container {
    display: flex;
    overflow-x: auto;
  }
}

::-webkit-scrollbar {
  display: none;
}
</style>