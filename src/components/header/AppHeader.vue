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
    <header>
        <div class="header-left">
            <strong class="logo">B</strong>
            <h1>Boolflix</h1>
        </div>
        <form action="" @submit.prevent="$emit('search')">
            <input class="input-text" type="text" v-model="store.searchText" placeholder="Cerca film o serie tv" @keyup="$emit('search')" required>
            <!-- <button type="submit">Cerca</button> -->
        </form>
    </header>
</template>

<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background-color: var( --primary-color);
    position: sticky;
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;

    .header-left {
        display: flex;
        align-items: center;

        .logo, h1 {
        color: var(--secondary-color);
        }
        .logo {
            margin-right: 1rem;
        }
    }
    .input-text {
        margin-right: 1rem;
        border-radius: .625rem;
        padding: 0.5rem;
        outline: none;
    }
}
</style>