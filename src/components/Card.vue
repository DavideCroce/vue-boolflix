<template>
  <div class="title-card">
      <ul>
          <li>
              <div class="poster">
                  <img :src="`https://image.tmdb.org/t/p/w185${item.poster_path}`" alt="">
              </div>
          </li>
          <li class="text">
              Titolo: {{item.title || item.name}}
          </li>
          <li class="text">
              Titolo originale: {{item.original_title || item.original_name}}
          </li>
          <li>
              <div class="flag">
                  <img v-if="flagslist.includes(item.original_language)" :src="flagResearch" alt="">
                  <span v-else>
                    {{item.original_language}}
                  </span>
              </div>
          </li>
          <li class="text">
              Voto: {{item.vote_average}}
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
  justify-content: center;
  flex-direction: column;
  background-color: black;
  align-items: center;
  height: 278px;

    li{
        list-style-type: none;
        text-align: center;
        margin: 10px 0;
    }
    // .text{
    //     width: 90%;
    // }
}
.poster img{
    position: absolute;
    top: 0;
    left: 0;
}
ul:hover .poster{
    cursor: pointer;
    display: none;
}

.flag{
    img{
        width: 20px;
    }
}
.title-card{
    width: 185px;
    margin: 20px;
    position: relative;
}
</style>