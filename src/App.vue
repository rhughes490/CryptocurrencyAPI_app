<template lang="html">
  <div>
    <coinclan-header title="CoinClan" />
    <coinclan-header v-if="!coins.length" title="LOADING..." />
    <h1>Check the Top 30 Cryptocurrency Coins</h1>
    <coin-filter-form :coins="coins" />
    <coin-detail />
    <coinclan-favourites-list :favourites="favourites"></coinclan-favourites-list>  

    <div class="main-container">
      <coins-list :coins="coins"></coins-list>
      <coin-detail :coin="selectedCoin"></coin-detail>
    </div>  
  </div>
</template>

<script>
import { eventBus } from '@/main.js';
import CoinDetail from '@/components/CoinDetail.vue';
import CoinList from '@/components/CoinList.vue';
import Header from "@/components/Header";
import FavouritesList from "@/components/FavouritesList";
import CoinFilterForm from '@/components/CoinFilterForm.vue';

export default {
  data(){
    return {
      coins: [],
      selectedCoin: null
    }
  },
    computed: {
    favourites: function() {
      return this.coins.filter(coin => coin.isFavourite);
    }
  },
  components: {
    "coinclan-header": Header,
    "coins-list": CoinList,
    "coin-detail": CoinDetail,
    "coin-filter-form": CoinFilterForm,
    "coinclan-favourites-list": FavouritesList
  },
  methods: {
    getCoins: function() {
      fetch("https://api.coingecko.com/api/v3/coins/markets?vs_currency=USD&order=market_cap_desc&per_page=30&page=1&sparkline=false")
        .then(res => res.json())
        .then(coinData => {
          coinData.forEach(coin => (coin.isFavourite = false));
          this.coins = coinData;
        })
    },
    markFavourite: function(coin) {
      const index = this.coins.indexOf(coin);
      this.coins[index].isFavourite = true;
    }
  },
  mounted() {
    this.getCoins();

    eventBus.$on("coin-selected", coin => (this.selectedCoin = coin));

    eventBus.$on("favourite-added", coin => this.markFavourite(coin));
  }
}
</script>

<style lang="css" scoped>
  h1 {
    text-align: center;
    color: #333;
  }
  .main-container {
    display: flex;
    justify-content: space-between;
    width: 80%;
    margin: 0 auto;
  }
</style>
