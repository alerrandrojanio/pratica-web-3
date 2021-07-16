<template>
    <Posts />
    <Albuns />
</template>

<script>
import axios from 'axios'
import Posts from './components/Posts.vue'
import Albuns from './components/Albuns.vue'

export default {
  name: 'App',
  components: {
    Posts,
    Albuns,
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
