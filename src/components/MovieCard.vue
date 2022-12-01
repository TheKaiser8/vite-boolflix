<script>
 export default {
    name: "MovieCard",
    props: {
        infoMovie: Object,
    }
 }
</script>

<template>
    <ul>
        <li>Titolo: {{ infoMovie.title }}</li>
        <li>Titolo originale: {{ infoMovie.original_title }}</li>
        <li>Lingua originale: {{ infoMovie.original_language }}</li>
        <li>Media voto: {{ infoMovie.vote_average }}</li>
    </ul>
</template>

<style lang="scss" scoped>
</style>