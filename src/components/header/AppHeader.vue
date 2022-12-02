<script>
import { store } from '../../store.js';

export default {
    name: 'AppHeader',
    emits: {
        search: null,
    },
    data() {
        return {
            store,
        }
    }
}
</script>

<template>
    <h1>Boolflix</h1>
    <form action="" @submit.prevent="$emit('search')">
        <input type="text" v-model="store.searchText" placeholder="Cerca film o serie tv" required>
        <button type="submit">Cerca</button>
    </form>
</template>

<style lang="scss" scoped>
</style>