<template>
<div class="container">
  <div class="search-bar">
    <input type="text" placeholder="Cerca un titolo..." >
    <button @click="searchMovies()">Cerca</button>
  </div>
  <div class="movies-list">
    <ul :for="movie in movies" :key="movie.title">
      <li>
        {{movie.title}}
        {{movie.original_title}}
        {{movie.original_language}}
        {{movie.vote_average}}
      </li>
    </ul>
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
      this.push(movies);
      });
    },
  },
}
</script>

<style lang="scss">

</style>
