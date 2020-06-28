<template lang="html">
  <div id="coinList">
    <ul>
      <list-component  v-for="(coin, index) in coins" :coin="coin" :key="index"></list-component>
    </ul>
  </div>

</template>

<script>
import ListComponent from './ListComponent.vue'
export default {
  name: 'coins-list',
  props: ['coins'],
  components: {
    "list-component": ListComponent
  }
}
</script>

<style lang="css" scoped>
  #coinsList {
    background: #eee;
    height: 400px;
    overflow-y: scroll;
    border: 1px solid #ccc;
  }

  #coinsList ul {
    margin: 10px;
    padding: 0;
  }

  ::-webkit-scrollbar {
    -webkit-appearance: none;
    width: 7px;
  }

  ::-webkit-scrollbar-thumb {
    border-radius: 4px;
    background-color: rgba(0,0,0,.5);
    -webkit-box-shadow: 0 0 1px rgba(255,255,255,.5);
  }
</style>
