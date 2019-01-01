<template>
    <div>
        <portfolio-stocks :key="stock" v-for="stock in stocks" :stock="stock"></portfolio-stocks>
    </div>
</template>

<script>
import {mapGetters} from 'vuex';
import Stock from './Stock.vue';

export default {
    computed: {
        ...mapGetters({
            stocks: 'stockPortfolio'
        })
    },
    components: {
        portfolioStocks: Stock
    }
}
</script>
