<template>
<div class="container">
  <div class="search-bar">
    <input type="text" placeholder="Cerca un titolo..." :for="movie in searchMovies()" :key="movie.title">
    <button>Cerca</button>
  </div>
</div>
</template>

<script>

export default {
  name: 'App',
  components: {
    
  },
  data(){
    return {
      movies: [],
    }
  },
  methods: {
    searchMovies(){
      axios.get("https://api.themoviedb.org/3/search/movie?api_key=c2b4899b88804168313526c583bf26b2&query=games&language=it-IT").then((res) => {
      this.movies = res.results.response;
      this.movie.push(movies);
      });
    },
  },
}
</script>

<style lang="scss">

</style>
