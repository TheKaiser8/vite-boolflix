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
}
</script>

<template>
    <div class="container">
        <AppHeader/>
        <AppMain/>
    </div>
</template>

<style lang="scss">
@import './style/global.scss';
</style>
