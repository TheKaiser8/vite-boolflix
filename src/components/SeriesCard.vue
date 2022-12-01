<script>
 export default {
    name: "SeriesCard",
    props: {
        infoSeries: Object,
    }
 }
</script>

<template>
    <ul>
        <li>Titolo: {{ infoSeries.name }}</li>
        <li>Titolo originale: {{ infoSeries.original_name }}</li>
        <li>Lingua originale: {{ infoSeries.original_language }}</li>
        <li>Media voto: {{ infoSeries.vote_average }}</li>
    </ul>
</template>

<style lang="scss" scoped>
</style>