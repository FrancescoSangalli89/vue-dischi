<template>
    <div class="col">
        <a href="#" class="card text-center my-card p-3 rounded-0 text-decoration-none">
            <img :src="album.poster" />
            <h5 class="mt-3 text-white">{{album.title}}</h5>
            <div class="text-muted">{{album.author}}</div>
            <div class="text-muted">{{album.year}}</div>
        </a>
    </div>
</template>

<script>
export default {
    name: 'SingleAlbum',
    props: {
        album: Object
    }
}
</script>

<style scoped lang="scss">

    @import '../styles/vars.scss';

    .my-card {
        height: 400px;
        background-color: $secondary-color;

        img {
            height: 250px;
        }

        h5 {
            text-transform: uppercase;
        }
    }
    

</style>