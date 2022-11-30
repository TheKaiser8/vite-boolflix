<script>
import { store } from '../../store.js';
import AppCard from '../common/AppCard.vue';
import AppCard from '../common/AppCard.vue';
 export default {
    name: "AppMain",
    components: "AppCard",
    data() {
        return {
            store
        };
    },
    components: { AppCard }
}
</script>

<template>
    <AppCard/>
</template>

<style lang="scss" scoped>
</style>