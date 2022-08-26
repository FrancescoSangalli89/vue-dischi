<template>
  <div id="app">
    <MyHeader />
    <AlbumsList />
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
  }
}
</script>

<style lang="scss">

  @import '@/styles/general.scss';

</style>