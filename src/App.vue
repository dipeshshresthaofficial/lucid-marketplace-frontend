<template>
  <HeaderComp />
  <ItemCardCont />
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import ItemCardCont from './components/ItemCardCont.vue';

export default {
  name: 'App',
  components: {
    HeaderComp,
    ItemCardCont,
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
*{
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin: 0 40px;
  /* display: flex;
  justify-content: center; */
}


</style>
