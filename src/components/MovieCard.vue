<script>
import CountryFlag from 'vue-country-flag-next';

 export default {
    name: "MovieCard",
    props: {
        infoMovie: Object,
    },
    components: {
        CountryFlag,
    },
    methods: {
        getLanguageFlag(lang) {
            if( lang === "en" ) {
                return "gb";
            } else if ( lang === "ja") {
                return "jp";
            } else if ( lang === "ko") {
                return "kr";
            } else if ( lang === "he") {
                return "il";
            } else if ( lang === "zh") {
                return "cn";
            } else if ( lang === "el") {
                return "gr";
            }
            return lang;
        }
    },
    computed: {
        getVote() {
            return Math.ceil(this.infoMovie.vote_average / 2);
        }
    }
 }
</script>

<template>
    <ul>
        <img :src="`https://image.tmdb.org/t/p/w342/${infoMovie.poster_path}`" :alt="infoMovie.title">
        <li>Titolo: {{ infoMovie.title }}</li>
        <li>Titolo originale: {{ infoMovie.original_title }}</li>
        <li>Lingua originale: 
            <country-flag :country='getLanguageFlag(infoMovie.original_language)' size='normal'/>
        </li>
        <li>Media voto: 
            <!-- v-for per creare stelle media voto -->
            <font-awesome-icon v-for="n in getVote" icon="fa-solid fa-star" />
            <!-- v-for per creare stelle stelle vuote se la media voto è diversa dal massimo (=5: 0 stelle vuote create)-->
            <font-awesome-icon v-for="n in (5 - getVote)" icon="fa-regular fa-star" />
        </li>
    </ul>
</template>

<style lang="scss" scoped>
</style>