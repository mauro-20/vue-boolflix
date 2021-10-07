<template>
  <div class="card">
    <img class="poster" 
      :src="details.poster_path ? `http://image.tmdb.org/t/p/w342/${details.poster_path}` : require('../assets/images/poster-placeholder.jpg')" 
      :alt="details.title||details.name">
    <div class="details">
      <h3>
        <i class="thin">Title: </i>
        {{details.title||details.name}}
        </h3>
      <h4>
        <i class="thin">Original Title: </i>
        {{details.original_title||details.original_name}}
        </h4>
      <div v-if="details.overview" class="overview">
        <i class="thin">Overview: </i>
        {{details.overview}}
        </div>
      <div>
        <i class="thin">Language: </i>
        <lang-flag v-if="flags.includes(details.original_language)" :iso="details.original_language" :squared="false" />
        <i v-else class="fas fa-globe-americas"></i>
      </div>
      <div>
        <i v-for="n in fullStars" :key="n" class="fas fa-star"></i>
        <i v-for="n in emptyStars" :key="n" class="far fa-star"></i>
      </div>
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
      emptyStars: null,
      flags: ['am', 'ar', 'az', 'bn', 'be', 'ca', 'cs', 'de', 'en', 'es', 'et', 'fa', 'fr', 'bg', 'ha', 'hi', 'hu', 'hy', 'it', 'ja', 'jv', 'km', 'ko', 'lv', 'mr', 'ms', 'pl', 'pt', 'ro', 'ru', 'sw', 'ta', 'te', 'th', 'tr', 'uk', 'uz', 'vi', 'zh']
    }
  },
  created(){
    this.fullStars = Math.ceil(this.details.vote_average / 2)
    this.emptyStars = 5 - this.fullStars
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variables.scss';

  .card{
    position: relative;
    width: 21.5625rem;
    height: 32.0625rem;
    margin: .625rem;
    
    img{
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    
    &:hover .details{
      display: inline-block;
    }
    .details{
      display: none;
      position: absolute;
      top: 0;
      right: 0;
      width: 100%;
      height: 100%;
      padding: 1.5625rem;
      color: $textLight;
      background-color: $bgColor;
      opacity: 0.85;

      *{
        margin-bottom: .625rem;
      }
      .thin{
        font-weight: 200;
      }
      .overview{
        max-height: 31ch;
        overflow-y: auto;
      }
      .fa-star{
        color: $starColor;
      }
    }
  }

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