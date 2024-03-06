<template>
  <img class="logo" alt="MTG logo" src="https://mtgproshop.com/wp-content/uploads/2021/05/MTG-PW-Symbol-Vector.png.webp">
  <HelloWorld msg="Welcome to MTG calculator" date=""/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>
<style>
body{
  background-color: #30363d;
}
.logo{
  height: 100px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 30px;
}
</style>
