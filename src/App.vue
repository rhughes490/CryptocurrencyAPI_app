<template lang="html">
  <div>
    <h1>Coins</h1>
    <div class="main-container">
      <coins-list :coins="coins"></coins-list>
      <coin-detail :coin="selectedCoin"></coin-detail>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import CoinDetail from './components/CoinDetail.vue'
import CoinList from './components/CoinList.vue'

export default {
  data(){
    return {
      coins: [],
      selectedCoin: null    }
  },
  components: {
    "coins-list": CoinList,
    "coin-detail": CoinDetail
  },
  mounted(){
    fetch('https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false&price_change_percentage=1h%2C24h%2C7d')
    .then(res => res.json())
    .then(coins => this.coins = coins)

    eventBus.$on('coin-selected', (coin) => {
      this.selectedCoin = coin
    })
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
