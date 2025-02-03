<template>
  <h1>Componentes</h1>
  <hr />
  <Card
    url="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fpic3.zhimg.com%2Fv2-d0aa5743d0f544474b78c3793266c2d8_1440w.jpg%3Fsource%3D172ae18b&f=1&nofb=1&ipt=0cd55d0bf657072b94a365f849e683e19e2e8742cdb884d11f95cef3f11fcab1&ipo=images"
    nombre="Vue.js"
  ></Card>
  <Card
    url="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fstatic-00.iconduck.com%2Fassets.00%2Fvuetify-icon-1793x2048-xtqk92sz.png&f=1&nofb=1&ipt=7bd43f254724ec4743a0922b08585091eb4d89dfd942591f20ddade06a9d8dde&ipo=images"
    nombre="Vuetify"
  ></Card>
</template>

<script>
import Card from "./components/Card.vue";
export default {
  components: {
    Card,
  },
};
</script>

<style>
</style>