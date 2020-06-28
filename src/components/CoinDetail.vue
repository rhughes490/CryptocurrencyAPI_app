<template lang="html">
  <div v-if="coin" id="coinDetail">
    <div id="detailWrapper">
      <h2>{{coin.name}}</h2>
      <div id="flexWrapper">
        <div id="left">
          <p><span>Symbol</span>: {{coin.symbol}}</p>
          <p><span>Current Price</span>: {{coin.current_price}} USD</p>
          <p><span>Percentage Change (24hrs)</span>: {{coin.price_change_percentage_24h}} %</p>
        </div>
        <div id="right">
          <img :src="coin.image" :alt="coin.name">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'coin-detail',
  props: ['coin']
}
</script>

<style lang="css" scoped>
  #coinDetail {
    box-sizing: border-box;
    height: 400px;
    width: 60%;
    background: #eee;
    color: #222;
    padding: 10px;
    border: 1px solid #ccc;
  }

  #detailWrapper {
    box-sizing: border-box;
    background: #fff;
    padding: 10px;
    height: 100%;
    border-radius: 3px;
  }

  #flexWrapper {
    display: flex;
    justify-content: space-between;
  }

  #left, #right {
    width: 45%;
  }

  #right img {
    width: 100%;
  }

  #left p:first-child {
    margin-top: 0;
  }

  h2 {
    margin: 10px 0 20px;
    padding: 0;
  }

  p span {
    font-weight: bold;
  }

</style>
