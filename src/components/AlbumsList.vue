<template>
  <div class="container my-5">

    <LoadInProgress v-if="loadInProgress" />

    <div v-else class="row row-cols-5 g-3">
        <SingleAlbum  v-for="(album, index) in albumsList" :key="index" :album="album" />
    </div>
    
    
  </div>
</template>

<script>

import axios from 'axios';
import SingleAlbum from './SingleAlbum.vue';
import LoadInProgress from './LoadInProgress.vue';

export default {
    name: 'AlbumsList',
    components: {
    SingleAlbum,
    LoadInProgress
},
    data() {
        return {
            albumsList: [],
            endpoint: 'https://flynn.boolean.careers/exercises/api/array/music',
            loadInProgress: true
        }
    },
    created() {
        axios.get(this.endpoint)
        .then(response => {
        this.albumsList = response.data.response;
        this.loadInProgress = false;
        })
        .catch(err => {
            console.log(err);
            this.loadInProgress = false;
        })
    }
}
</script>

<style>

</style>