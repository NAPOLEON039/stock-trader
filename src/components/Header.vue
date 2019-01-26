<template>
    <nav class="navbar navbar-default">
        <div class="container-fluid">
            <div class="navbar-header">
                <router-link to="/" class="navbar-brand">Stock Trader</router-link>
            </div>
            <div class="collapse navbar-collapse">
                <ul class="nav navbar-nav">
                    <router-link to="/portfolio" tag="li" activeClass="active"><a>Portfolio</a></router-link>
                    <router-link to="/stocks" tag="li" activeClass="active"><a>Stocks</a></router-link>
                </ul>
                <strong class="navbar-text navbar-right">Funds: {{  funds | currency }}</strong>
                <ul class="nav navbar-nav navbar-right">
                    <li><a href="#" @click="endDay">End Day</a></li>
                    <li class="dropdown" :class="{open: isDropdownOpen}" @click="isDropdownOpen = !isDropdownOpen">
                        <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">
                            Save and Load<span class="caret"></span>
                        </a>
                        <ul class="dropdown-menu">
                            <li><a href="#" @click="saveData">Save Data</a></li>
                            <li><a href="#" @click="loadData">Load Data</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
import {mapActions} from 'vuex';
export default {
    data() {
        return {
            isDropdownOpen: false
        }
    },
    computed: {
        funds() {
            return this.$store.getters.funds;
        }
    },
    methods: {
        ...mapActions([
            'randomizeStocks'
        ]),
        endDay() {
            this.randomizeStocks();
        },
        saveData() {
            const data = {
                funds: this.$store.getters.funds,
                stockPortoflio: this.$store.getters.stockPortoflio,
                stocks: this.$store.getters.stocks
            };
            //using the put method with Firebase db replaces existing data with a new one. This is fine in this case where we only care about our recent data
            this.$http.put('data.json', data); 
        },
        loadData() {
            
        }
    }
}
</script>
