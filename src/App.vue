<template>
<!-- only one parent inside template so only div -->
  <div id="app">Getting started with Vuejs
  <div id="app">
    Getting started with Vuejs
    <hello-world></hello-world>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
export default {
  name: "app",
  

  data() {
    return {
      message: ""
    };
  },
  components: {
    HelloWorld
  }
};
</script>

<style lang="scss">
@import "./styles/main.scss";

#app {
  margin-top: 60px;
}
</style>
