<template>
  <div id="app">
    <MyHeader :genresList="genres" @changedGenre="startSearch" />
    <AlbumsList @genresReady="getGenresList" :genreToSearch="selectedGenre" />
  </div>
</template>

<script>

import MyHeader from './components/MyHeader.vue';
import AlbumsList from './components/AlbumsList.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    AlbumsList
  },
  data() {
    return {
      genres: [],
      selectedGenre: "Seleziona un genere"
    }
  },
  methods: {
    getGenresList(genresList) {
      this.genres = genresList;
    },
    startSearch(selectedGenre) {
      this.selectedGenre = selectedGenre;
      console.log(selectedGenre);
    }
  }
}
</script>

<style lang="scss">

  @import '@/styles/general.scss';

</style>