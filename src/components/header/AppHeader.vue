<script>
import { store } from '../../store.js';
 export default {
    name: 'AppHeader',
    data() {
        return {
            store
        }
    }
 }
</script>

<template>
    <h1>Boolflix</h1>
    <form action="">
        <input type="text" placeholder="Cerca titolo film">
        <button type="submit">Cerca</button>
    </form>
</template>

<style lang="scss" scoped>
</style>