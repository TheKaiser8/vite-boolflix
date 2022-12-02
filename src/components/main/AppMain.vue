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
        <div class="movies">
            <h4>Film trovati ({{ store.movies.length }}):</h4>
            <div class="row">
                <AppCard 
                v-for="movie in store.movies" 
                :info="movie"
                class="card-item"
                />
            </div>
        </div>
        <div class="series">
            <h4>Serie TV trovate ({{ store.series.length }}):</h4>
            <div class="row">
                <AppCard 
                v-for="serie in store.series" 
                :info="serie"
                class="card-item"
                />
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
#main-page {
    display: flex;
    flex-direction: column;
    padding: 1rem;
    color: var(--first-text-color);

    .row {
        display: flex;
        flex-wrap: wrap;
    }

    .card-item {
        width: calc(100% / 6);
        height: 100%;
        padding: 1.5rem;
        border-bottom: 1px solid black;
}
}

</style>