<template>
  <div class="search-bar">
    <input type="text" placeholder="Cerca un titolo..." v-model="query" @keyup.enter="search()">
    <button @click="search()">CERCA UN TITOLO</button>
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

<style scoped lang="scss">
button{
    background-color: red;
    color: white;
    padding: 10px;
    border: none;
}
input{
    border: none;
    padding: 10px;
    background-color: rgb(114, 114, 114);
    color: white;
}

::placeholder {
color: #fff;
}

</style>