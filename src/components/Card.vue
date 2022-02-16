<template>
  <div class="title-card">
      <ul>
          <li>
              <div class="poster">
                  <img :src="`https://image.tmdb.org/t/p/w185${item.poster_path}`" alt="">
              </div>
          </li>
          <li class="text">
              <strong>Titolo</strong>: {{item.title || item.name}}
          </li>
          <li class="text">
              <strong>Titolo originale</strong>: {{item.original_title || item.original_name}}
          </li>
          <li>
              <div class="flag">
                  <strong>Lingua originale</strong>: <img v-if="flagslist.includes(item.original_language)" :src="flagResearch" alt="">
                  <span v-else>
                    <strong>Lingua originale</strong>: {{item.original_language}}
                  </span>
              </div>
          </li>
          <li class="text">
              <strong>Voto</strong>: {{voteConvert}}
          </li>
      </ul>
  </div>
</template>

<script>
export default {
name: 'Card',
props: ['item'],
data(){
    return{
        flagslist:['de', 'en', 'es', 'fr', 'it', 'jp', 'pt', 'ru']
    }
},
computed: {
    flagResearch(){
        return require(`../assets/flags/${this.item.original_language}.png`);
    },
    voteConvert(){
        return Math.floor(this.item.vote_average / 2);
    },
},
}
</script>

<style scoped lang="scss">
ul{
  display: flex;
  flex-direction: column;
  background-color: black;
  height: 278px;

    li{
        list-style-type: none;
        margin: 10px 0;
    }
}
.poster img{
    position: absolute;
    top: 0;
    left: 0;
    height: 278px;
}
ul:hover .poster{
    cursor: pointer;
    display: none;
}

.flag{
    margin-left: 10px;
    img{
        width: 20px;
    }
}
.title-card{
    width: 185px;
    margin: 20px;
    position: relative;
}
.text{
    width: 90%;
    margin-left: 10px;
}
</style>