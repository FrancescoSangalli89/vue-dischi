<template>
    <header>
        <a href="#">
            <img class="p-2" src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/2048px-Spotify_logo_without_text.svg.png" alt="spotify logo" />
        </a>
        <div>
            <select class="form-select" v-model="selectedGenre" @change="$emit('changedGenre', selectedGenre)" >
                <option selected>Seleziona un genere</option>
                <option v-for="(genre, index) in genresList" :key="index" :value=genre>{{genre}}</option>
            </select>
        </div>
    </header>
</template>

<script>

export default {
    name: 'MyHeader',
    props: {
        genresList: Array,
    },
    data() {
        return {
            selectedGenre: "Seleziona un genere"
        }
    }
}
</script>

<style scoped lang="scss">
    @import '@/styles/vars.scss';

    header {
        height: 50px;
        background-color: $secondary-color;
        display: flex;
        justify-content: space-between;
        align-items: center;

        img {
            max-height: 50px;
        }
    }
</style>