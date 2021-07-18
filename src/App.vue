<template>
    <button @click="reload">App</button>
    <Posts />
    <Albuns />
    <Photos />
    <Todos />
</template>

<script>
import Posts from './components/Posts.vue'
import Albuns from './components/Albuns.vue'
import Photos from './components/Photos.vue'
import Todos from './components/Todos.vue'

export default {
  name: 'App',
  components: {
    Posts,
    Albuns,
    Photos,
    Todos,
    
  },
  methods: {
    reload: function(){
      window.location.reload()
    }
  },
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

li {
  text-align: left;
}
</style>
