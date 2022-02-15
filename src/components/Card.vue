<template>
  <div class="title-card">
      <ul>
          <li>
              {{item.title || item.name}}
              {{item.original_title || item.original_name}}
              <div class="flag">
                  <img v-if="flags.includes(item.original_language)" :src="flagResearch" alt="">
                  <span v-else>
                    {{item.original_language}}
                  </span>
              </div>
              {{item.vote_average}}
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
    }
}
}
</script>

<style scoped lang="scss">
li{
  list-style-type: none;
}
img{
  width: 20px;
}
</style>