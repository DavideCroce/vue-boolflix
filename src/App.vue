<template>
<div class="container">
  <header>
    <img src="./assets/img/boolflix.png" alt="">
    <Search/>
  </header>
  <main>
    <div class="movies-list" v-if="movies.length">
    <h1>Film</h1>
    <Card v-for="movie in movies" :key="movie.id" :item="movie"/>
  </div>
  <div class="series-list" v-if="series.length">
    <h1>Serie TV</h1>
    <Card v-for="serie in series" :key="serie.id" :item="serie"/>
  </div>
  </main>
</div>
</template>

<script>
import Card from './components/Card.vue';
import Search from './components/Search.vue';
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
  width: 100vw;
  height: 100vh;
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
