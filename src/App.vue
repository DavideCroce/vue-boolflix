<template>
<div class="container">
  <div class="search-bar">
    <input type="text" placeholder="Cerca un titolo..." v-model="searchResult">
    <button @click="searchMovies()">Cerca film</button>
    <button @click="searchSeries()">Cerca serie</button>
  </div>
  <div class="movies-list" v-if="movies.length">
    <h1>Film</h1>
    <ul v-for="movie in movies" :key="movie.title" >
      <li>
        {{movie.title}} -
        {{movie.original_title}} -
        {{movie.original_language}} -
        {{movie.vote_average}}
      </li>
    </ul>
  </div>
  <div class="series-list" v-if="series.length">
    <h1>Serie TV</h1>
    <ul v-for="serie in series" :key="serie.title">
      <li>
        {{serie.name}}
        {{serie.original_name}}
        {{serie.original_language}}
        {{serie.vote_average}}
      </li>
    </ul>
  </div>
</div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'App',
  components: {
    
  },
  data(){
    return {
      movies: [],
      series: [],
      query: '',
      apiKey: "c2b4899b88804168313526c583bf26b2",
    }
  },
  methods: {
    searched(search){
      this.searchResult = search;
    },
    searchMovies(){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.query}&language=it-IT`).then((res) => {
      this.movies = res.data.results;});
    },
    searchSeries(){
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${this.query}&language=it-IT`).then((res) => {
      this.series = res.data.results;});
    },
    realSearch(){
      this.$emit("query-search-movie", this.searchResult);
      this.$emit("query-search-tv", this.searchResult);
      this.searchResult = "";
    }
  },
}
</script>

<style lang="scss">
body{
  font-family: sans-serif;
}
li{
  list-style-type: none;
}
</style>
