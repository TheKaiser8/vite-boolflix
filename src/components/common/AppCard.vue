<script>
import CountryFlag from 'vue-country-flag-next';

 export default {
    name: "AppCard",
    props: {
        info: Object,
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
            } else if ( lang === "da") {
                return "dk";
            } else if ( lang === "cs") {
                return "cz";
            } else if ( lang === "uk") {
                return "ua";
            } 
            return lang;
        }
    },
    computed: {
        getVote() {
            return Math.ceil(this.info.vote_average / 2);
        },
        // funzione come variabile per ottenere un placeholder quando non è presente l'immagine copertina
        posterImage() {
            return this.info.poster_path 
            ? `https://image.tmdb.org/t/p/w342/${this.info.poster_path}` 
            : "https://via.placeholder.com/342x513";
        },
    }
 }
</script>

<template>
    <ul>
        <img :src="posterImage" :alt="info.title || info.name">
        <div class="info-card">
            <li><strong>Titolo: </strong>{{ info.title || info.name }}</li>
            <li><strong>Titolo originale: </strong>{{ info.original_title || info.original_name }}</li>
            <li><strong>Lingua originale: </strong> 
                <country-flag :country='getLanguageFlag(info.original_language)' size='normal'/>
            </li>
            <li><strong>Media voto: </strong> 
                <!-- v-for per creare stelle media voto -->
                <font-awesome-icon v-for="n in getVote" icon="fa-solid fa-star" class="gold-icon" />
                <!-- v-for per creare stelle stelle vuote se la media voto è diversa dal massimo (=5: 0 stelle vuote create)-->
                <font-awesome-icon v-for="n in (5 - getVote)" icon="fa-regular fa-star" />
            </li>
            <li class="overview" v-if="info.overview != ''"><strong>Descrizione: </strong> {{ info.overview }}</li>
        </div>
    </ul>
</template>

<style lang="scss" scoped>
ul {
    position: relative;
    cursor: pointer;
    list-style: none;

    img {
        max-width: 100%;
        max-height: 100%;
        object-fit: cover;
    }

    .info-card {
        display: none;
        position: absolute;
        padding: 1.5rem;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        overflow: hidden;

        li {
            margin-bottom: .5rem;

            .gold-icon {
                color: gold;
            }
            &.overview {
            max-height: 18rem;
            display: -webkit-box;
            -webkit-line-clamp: 14;
            -webkit-box-orient: vertical;
            overflow-y: hidden;
            text-overflow: ellipsis;
        }
        }
    }
    &:hover .info-card {
        display: block;
    }

    &:hover img {
        filter: opacity(0.3);
    }
}
</style>