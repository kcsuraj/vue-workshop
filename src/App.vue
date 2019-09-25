<template>
  <div id="app">
    <CalculatorMovie />
  </div>
</template>

<script>
import CalculatorMovie from "./components/CalculatorMovie.vue";

export default {
  name: "app",
  components: {
    CalculatorMovie
  }
};
</script>

<style lang="scss">
@import "./styles/main.scss";

#app {
  margin-top: 60px;
}
</style>