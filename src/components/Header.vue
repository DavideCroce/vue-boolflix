<template>
  <div class="header">
      <img src="../assets/img/boolflix.png" alt="">
      <Search/>
  </div>
</template>

<script>
import Search from './Search.vue';
export default {
name: 'Header',
components: {
    Search,
}
}
</script>

<style scoped lang="scss">
.header{
    background-color: rgb(46, 45, 45);
    height: 100px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}
img{
    height: 80px;
    width: 250px;
}
</style>