<template lang="html">
  <li>{{ coin.name }} <button v-on:click="selectCoin">Display Info</button></li>
</template>

<script>
import { eventBus } from "@/main";

export default {
  props: ["coin"],
  methods: {
    selectCoin: function() {
      eventBus.$emit("coin-selected", this.coin);
    }
  }
};
</script>

<style lang="css" scoped>

li {
  display: inline;
  padding-right: 10px;
}

button {
  padding: 10px;
  font: bold 11px Futura;
  text-decoration: none;
  background-color: #EEEEEE;
  color: #333333;
  padding: 2px 6px 2px 6px;
  border-top: 1px solid #CCCCCC;
  border-right: 1px solid #333333;
  border-bottom: 1px solid #333333;
  border-left: 1px solid #CCCCCC;
}
</style>
