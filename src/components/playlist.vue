<template>
  <section>
    <h2>Everyday Essentials</h2>
    <form @submit="addSong">
      <label for="new-song">
        Add a new song!
        <input type="text" name="new-song" v-model="newSong" />
        <input type="text" name="new-artist" v-model="newArtist" />
      </label>
      <input type="submit" value="Save a new song" />
      <br />
    </form>
    <ul>
      <Song
        v-for="song in songs"
        :key="song.name"
        :song="song"
        v-on:played-song="playedSong"
        v-on:delete-song="removeSong"
        v-on:like-song="likeSong"
        :class="{'liked-song' : song.favorite}"
      />
    </ul>
  </section>
</template>

<script>
import Song from "./song.vue";

export default {
  name: "Playlist",
  components: {
    Song
  },
  data() {
    return {
      newSong: "",
      songs: [
        {
          name: "Wouldn't it be nice..",
          artist: "The Beach Boys",
          played: false
        },
        {
          name: "Iktara",
          artist: "Arijit Singh",
          played: false
        },
        {
          name: "Frieflies",
          artist: "When Chai met Toast",
          played: false
        }
      ]
    };
  },
  methods: {
    playedSong(song) {
      const songIndex = this.songs.indexOf(song);
      this.songs[songIndex].played = true;
    },
    addSong(event) {
      event.preventDefault();
      const newSong = this.newSong;
      const newArtist = this.newArtist;
      this.songs.push({
        name: newSong,
        artist: newArtist,
        played: false
      });

      this.newSong = "";
    },
    likeSong(song) {
      const faveIndex = this.songs.indexOf(song);
      this.songs[faveIndex].favorite = !this.songs[faveIndex].favorite;
    },
    removeSong(song) {
      const songIndex = this.songs.indexOf(song);
      this.songs.splice(songIndex, 1);
    }
  }
};
</script>

<style>
.liked-song {
    font-weight: bold;
    color: lightblue;
  }
</style>