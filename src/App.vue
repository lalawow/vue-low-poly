<template>
 <div id="app">
  <VueLowPoly :accuracy="accuracy" src="./bird-01.jpg"/>
  <button @click="change">refresh</button>
 </div>
</template>

<script>
import VueLowPoly from "./components/index.js";

export default {
  name: "app",
  components: {
    VueLowPoly
  },
  data() {
    return {
      accuracy: 75
    };
  },
  methods: {
    change() {
      console.log("click");
      this.accuracy = parseInt(Math.random() * 100);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
