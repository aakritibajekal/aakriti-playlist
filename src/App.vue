<template>
  <div id="app">
    <h1>Aakriti's Playlist</h1>
    <Playlist />
  </div>
</template>

<script>
import Playlist from './components/playlist.vue'

export default {
  name: 'App',
  components: {
   Playlist
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
