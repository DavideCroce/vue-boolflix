<template>
<div class="container">
  <Header/>
  <main></main>
  <div class="movies-list" v-if="movies.length">
    <h1>Film</h1>
    <Card v-for="movie in movies" :key="movie.id" :item="movie"/>
  </div>
  <div class="series-list" v-if="series.length">
    <h1>Serie TV</h1>
    <Card v-for="serie in series" :key="serie.id" :item="serie"/>
  </div>
</div>
</template>

<script>
import Header from './components/Header.vue';
import Card from './components/Card.vue';
export default {
  name: 'App',
  components: {
    Card,
    Header,
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
    noSearch(){
      if(!this.query){
        return 'Cerca un titolo';
      }
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
*{
  padding: 0;
  margin: 0 auto;
  box-sizing: border-box;
}
body{
  font-family: sans-serif;
}
li{
  list-style-type: none;
}
img{
  width: 20px;
}
main{
  background-color: rgb(75, 75, 75);
  width: 100%;
  height: 100%;
}
</style>
