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
    computed: {
        getResults() {
            return ((store.movies.length > 0 || store.series.length > 0) & store.searchText != '');
        },
        getNoResults() {
            return ((store.movies.length <= 0 & store.series.length <= 0) & store.searchText != '');
        }
    }
}
</script>

<template>
    <main>
        <div class="page-result" v-if="getResults">
            <h3>Risultati trovati per "{{ store.searchText }}"</h3>
            <section class="movies">
                <h4 v-if="store.movies.length > 0">Film trovati ({{ store.movies.length }}):</h4>
                <h4 v-else>Nessuna serie TV trovata</h4>
                <div class="row">
                    <AppCard 
                    v-for="movie in store.movies" 
                    :info="movie"
                    class="card-item"
                    />
                </div>
            </section>
            <section class="series">
                <h4 v-if="store.series.length > 0">Serie TV trovate ({{ store.series.length }}):</h4>
                <h4 v-else>Nessuna serie TV trovata</h4>
                <div class="row">
                    <AppCard 
                    v-for="serie in store.series" 
                    :info="serie"
                    class="card-item"
                    />
                </div>
            </section>
        </div>
        <div class="page-no-results" v-else-if="getNoResults">
            <h3>Nessun film o serie tv trovati per "{{ store.searchText }}""</h3>
        </div>
    </main>
</template>

<style lang="scss" scoped>
main {
    display: flex;
    flex-direction: column;
    padding: 1rem;
    color: var(--first-text-color);

    .row {
        display: flex;
        flex-wrap: wrap;
    }

    .movies, .series {
        margin: 1.5rem 0;
    }
    .card-item {
        width: calc(100% / 6);
        height: 100%;
        padding: 1.5rem;
        border-bottom: 1px solid black;
    }
}
</style>