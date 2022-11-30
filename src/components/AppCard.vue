<script>
 export default {
    name: "AppCard",
    props: {
        info: Object,
    }
 }
</script>

<template>
    <ul class="card-item">
        <li>Titolo: {{ info.title }}</li>
        <li>Titolo originale: {{ info.original_title }}</li>
        <li>Lingua originale: {{ info.original_language }}</li>
        <li>Media voto: {{ info.voto_average }}</li>
    </ul>
</template>

<style lang="scss" scoped>
.card-item {
    margin: 1rem 0;
}
</style>