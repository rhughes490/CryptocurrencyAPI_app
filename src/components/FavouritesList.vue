<template lang="html">
  <div id="favourites-list">
    <ul>
      <coinclan-favourites-listitem
        v-for="(coin, index) in favourites"
        :coin="coin"
        :key="index"
      ></coinclan-favourites-listitem>
    </ul>
  </div>
</template>

<script>
import FavouritesListitem from "@/components/FavouritesListItem";
import Header from "@/components/Header";

export default {
  props: ["favourites"],
  components: {
    "coinclan-favourites-listitem": FavouritesListitem,
    "coinclan-header": Header
  }
};
</script>

<style lang="css" scoped>

ul {
  padding: 20px;
}

coinclan-favourites-listitem {
  font: 5px;
}

</style>
