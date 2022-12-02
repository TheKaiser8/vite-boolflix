<script>
import axios from 'axios';
import { store } from './store.js';
import AppHeader from './components/header/AppHeader.vue';
import AppMain from './components/main/AppMain.vue';

export default {
    components: {
        AppHeader,
        AppMain
    },
    data() {
        return {
            store
        }
    },
    methods: {
        getMoviesAndSeries() {
            axios
                .get('https://api.themoviedb.org/3/search/movie', {
                    params: {
                        api_key: '87b824cd69d9f0f761fc248783d4e988',
                        language: 'it-IT',
                        query: this.store.searchText,
                    }
                })
                .then((response) => {
                    console.log(response.data.results);
                    this.store.movies = response.data.results;
                    console.log(this.store.movies);
                }),
            axios
                .get('https://api.themoviedb.org/3/search/tv', {
                    params: {
                        api_key: '87b824cd69d9f0f761fc248783d4e988',
                        language: 'it-IT',
                        query: this.store.searchText,
                    }
                })
                .then((response) => {
                    console.log(response.data.results);
                    this.store.series = response.data.results;
                    console.log(this.store.series);
                })
        }
    }
}
</script>

<template>
    <div class="container">
        <AppHeader @search="getMoviesAndSeries" />
        <AppMain/>
    </div>
</template>

<style lang="scss">
@import './style/global.scss';
</style>
