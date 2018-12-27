<template>
    <div>
        <app-stock :key="stock" v-for="stock in stocks" :stock="stock"></app-stock>
    </div>
</template>

<script>
import Stock from './Stock.vue';

export default {
    components: {
        appStock: Stock
    },
    computed: {
        stocks() {
            this.$store.getters.getStocks;
        }
    }
}
</script>
