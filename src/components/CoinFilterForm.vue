<template lang="html">
  <form v-on:submit.prevent>
    <input type="text" v-model="search" placeholder="search for coin..." v-on:keyup="searchForCoin">
    <select v-on:change="handleSelect" v-model="selectedCoin">
      <option disabled value="">Select a coin...</option>
      <option v-for="coin in coins" :value="coin">{{coin.name}}</option>
    </select>
  </form>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: "coin-filter-form",
  data(){
    return {
      "search": "",
      "selectedCoin": {},
    }
  },
  props: ["coins"],
  methods: {
    searchForCoin(){
      let foundCoin = this.coins.find((coin) => {
        return coin.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedCoin = foundCoin

      eventBus.$emit('coin-selected', this.selectedCoin)
    },
    handleSelect(){
      this.search = ""
      eventBus.$emit('coin-selected', this.selectedCoin)
    }
  }
}
</script>

<style lang="css" scoped>
form{
  text-align: center;
  margin: 40px 0;
}

select, input[type="text"]{
  font-size: 18px;
}

select {
  margin-left: 20px;
}
</style>
