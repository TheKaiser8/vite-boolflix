<script>
import axios from 'axios';
import { store } from './store.js';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

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
        getMovies() {
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
                })
        }
    }
}
</script>

<template>
    <div class="container">
        <AppHeader @search="getMovies" />
        <AppMain/>
    </div>
</template>

<style lang="scss">
@import './style/global.scss';
</style>
