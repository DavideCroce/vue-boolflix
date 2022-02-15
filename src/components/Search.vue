<template>
  <div class="search-bar">
    <input type="text" placeholder="Cerca un titolo..." v-model="query" @keyup.enter="search()">
    <button @click="search()">Cerca un titolo</button>
  </div>
</template>

<script>
export default {
name: 'Search',
data(){
    return{
      query: '',
    };
},
methods: {
    search(){
        this.$emit('research', this.query);
    },
}
}
</script>

<style>

</style>