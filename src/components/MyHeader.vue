<template>
    <header>
        <img class="p-2" src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/2048px-Spotify_logo_without_text.svg.png" alt="spotify logo" />
    </header>
</template>

<script>
export default {
    name: 'MyHeader'
}
</script>

<style scoped lang="scss">
    @import '@/styles/vars.scss';

    header {
        height: 50px;
        background-color: $secondary-color;

        img {
            height: 100%;
        }
    }
</style>