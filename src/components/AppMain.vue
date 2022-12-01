<script>
import { store } from '../store.js';
import MovieCard from './MovieCard.vue';
import SeriesCard from './SeriesCard.vue';

export default {
    name: "AppMain",
    components: {
        MovieCard,
        SeriesCard,
    },
    data() {
        return {
            store
        };
    },
}
</script>

<template>
    <div id="main-page" v-if="(store.movies.length > 0 || store.series.length > 0)">
        <h3>Risultati trovati per "{{ store.searchText }}"</h3>
        <div class="movies-container">
            <h4>Film trovati ({{ store.movies.length }}):</h4>
            <MovieCard 
            v-for="movie in store.movies" 
            :infoMovie="movie"
            class="card-item"
            />
        </div>
        <div class="series-container">
            <h4>Serie TV trovate ({{ store.series.length }}):</h4>
            <SeriesCard 
            v-for="serie in store.series" 
            :infoSeries="serie"
            class="card-item"
            />
        </div>
    </div>
</template>

<style lang="scss" scoped>
#main-page {
    display: flex;

    .movies-container, .series-container, h3 {
        width: auto;
        margin: 2rem;
    }
    .movies-container {
        background-color: lightgreen;
    }
    .series-container {
        background-color: lightblue;
    }

    .card-item {
        padding: 1.5rem;
        border-bottom: 1px solid black;
}
}

</style>