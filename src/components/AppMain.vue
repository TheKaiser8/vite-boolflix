<script>
import { store } from '../store.js';
import AppCard from './AppCard.vue';

export default {
    name: "AppMain",
    components: "AppCard",
    data() {
        return {
            store
        };
    },
}
</script>

<template>
    <AppCard 
    v-for="movie in store.movies" 
    :info="movie"
    />
</template>

<style lang="scss" scoped>
</style>