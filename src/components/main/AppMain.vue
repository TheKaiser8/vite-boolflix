<script>
import { store } from '../../store.js';
import AppCard from '../common/AppCard.vue';

export default {
    name: "AppMain",
    components: {
        AppCard,
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
            <AppCard 
            v-for="movie in store.movies" 
            :info="movie"
            class="card-item"
            />
        </div>
        <div class="series-container">
            <h4>Serie TV trovate ({{ store.series.length }}):</h4>
            <AppCard 
            v-for="serie in store.series" 
            :info="serie"
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