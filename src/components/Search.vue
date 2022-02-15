<template>
  <div class="search-bar">
    <input type="text" placeholder="Cerca un titolo..." v-model="query" @keyup.enter="searchMovies(), searchSeries(), noSearch()">
    <button @click="searchMovies(),searchSeries()" >Cerca un titolo</button>
  </div>
</template>

<script>
import axios from 'axios';
export default {
name: 'Search',
data(){
    return{
      query: '',
      apiKey: "c2b4899b88804168313526c583bf26b2",
    };
},
methods: {
    searchMovies(){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.query}&language=it-IT`).then((res) => {
      this.movies = res.data.results;});
    },
    searchSeries(){
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${this.query}&language=it-IT`).then((res) => {
      this.series = res.data.results;});
    },
}
}
</script>

<style>

</style>