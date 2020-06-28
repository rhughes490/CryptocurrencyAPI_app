<template>
  <h2>{{ title }}</h2>
</template>

<script>
export default {
  name: "coinclan-header",
  props: ["title"]
};
</script>

<style scoped>
h2 {
  font: bold 50px titillium;
  color:limegreen;
  text-align: center;
  background-color: black;
  padding: 5px;
}
</style>
