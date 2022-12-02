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
    <AppHeader @search="getMoviesAndSeries" />
    
    <AppMain/>
</template>

<style lang="scss">
@import './style/global.scss';
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,300;0,400;0,500;0,700;0,900;1,400&display=swap');

body {
    background-color: var(--primary-color);
}
</style>
