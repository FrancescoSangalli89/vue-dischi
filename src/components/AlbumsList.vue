<template>
  <div class="container my-5">

    <LoadInProgress v-if="loadInProgress" />

    <div v-else class="row row-cols-5 g-3">
        <SingleAlbum  v-for="(album, index) in getFilteredalbums" :key="index" :album="album" />
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
    props: {
        genreToSearch: String
    },
    data() {
        return {
            albumsList: [],
            genres: [],
            endpoint: 'https://flynn.boolean.careers/exercises/api/array/music',
            loadInProgress: true
        }
    },
    computed: {
        getFilteredalbums() {
            
            if (this.genreToSearch == '') {
                return this.albumsList;
            } else {
                const filteredValue = this.albumsList.filter((album => {
                    if (album.genre.includes(this.genreToSearch)) {
                        return true;
                    } else {
                        return false;
                    }
                }));  

                return filteredValue;

            }
        }
    },
    created() {
        axios.get(this.endpoint)
        .then(response => {
        this.albumsList = response.data.response;
        this.genres = this.getGenres(this.albumsList);
        this.$emit("genresReady",this.genres);
        this.loadInProgress = false;
        })
        .catch(err => {
            console.log(err);
            this.loadInProgress = false;
        })
    },
    methods: {
        getGenres(genres) {
            let scopeGenres = this.genres;
            for (let i = 0; i < genres.length; i++) {
                console.log(genres[i].genre);
                scopeGenres.push(genres[i].genre);
                let uniqueGenres = [...new Set(scopeGenres.sort())];
                scopeGenres = uniqueGenres;
            }
            return(scopeGenres);
        }
    }
}
</script>

<style>

</style>