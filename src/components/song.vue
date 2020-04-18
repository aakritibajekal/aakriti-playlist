<template>
<li v-if="!song.played">
    {{ song.name + " by " + song.artist }}
    <button class="unliked-button" v-if="!song.favorite" @click="likeSong( song )">Add to Favourites</button>
    <button class="liked-button" v-else @click="likeSong( song )">Love this song!</button>
    <button v-on:click="removeSong( song )">Bored of this song</button> 
  </li>
</template>

<script>
export default {
  name: "Song",
  props: ["song"], 
  methods: {
    playedSong(song) {
      this.$emit("played-song", song);
    },
    removeSong(song) {
    this.$emit("delete-song", song);
  },
    likeSong(song) {
      this.$emit("like-song", song);
    }
  }
};
</script>

<style>
.liked-button {
 color: lightblue;
 font: bold;
}
</style>