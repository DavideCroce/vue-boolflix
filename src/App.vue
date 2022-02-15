<template>
<div class="container">
  <header>
    <img src="./assets/img/boolflix.png" alt="">
    <Search @research="search"/>
  </header>
  <main>
    <h1>FILM</h1>
    <div class="movies-list" v-if="movies.length">
    <Card v-for="movie in movies" :key="movie.id" :item="movie"/>
  </div>
    <h1>SERIE TV</h1>
  <div class="series-list" v-if="series.length">
    <Card v-for="serie in series" :key="serie.id" :item="serie"/>
  </div>
  </main>
</div>
</template>

<script>
import Card from './components/Card.vue';
import Search from './components/Search.vue';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    Card,
    Search,
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
    search(value){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${value}&language=it-IT`).then((res) => {
      this.movies = res.data.results;});
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${value}&language=it-IT`).then((res) => {
      this.series = res.data.results;});
    },
}
}
</script>

<style lang="scss">
*{
  padding: 0;
  margin: 0 auto;
  box-sizing: border-box;
}
body{
  font-family: sans-serif;
}
main{
  background-color: rgb(75, 75, 75);
  width: 100%;
  height: 100%;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-top: 100px;
  .movies-list, .series-list{
    color: white;
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    margin-bottom: 200px;
    margin-left: 100px;
  }
  h1{
    color: red;
    padding-bottom: 50px;
  }
}
header{
  background-color: rgb(46, 45, 45);
  height: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  img{
    height: 80px;
    width: 250px;
  }
}
</style>
