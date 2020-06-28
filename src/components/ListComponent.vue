<template lang="html">
  <div class="coinlistitem">
    <p>{{ coin.name }}</p>
    <button v-on:click="displayInfo">More Info</button>
    <button v-on:click="addFavourite">Add to Favourites</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-component',
  props: ['coin'],
  methods: {
    displayInfo(){
      eventBus.$emit('coin-selected', this.coin);
    },
    addFavourite: function() {
      eventBus.$emit("favourite-added", this.coin);
    }
  }
};
</script>

<style lang="css" scoped>
  li {
    list-style-type: none;
    display: block;
    background: #fff;
    font-size: 16px;
    margin: 10px 0;
    padding: 10px;
    cursor: pointer;
    color: #555;
    transition: 0.1s all ease-in;
    border-radius: 3px;
  }

button {
  background-color: #4CAF50;
  border-radius: 10%;
  color: white;
  margin: 0px 10px;
  text-align: center;
  display: inline-block;
  font-size: 12px;
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
}

button:hover {
  background-color: white;
  color: black;
}
</style>
