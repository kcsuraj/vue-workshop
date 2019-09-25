<template>
  <div id="app">
    <netflix-ratings />
  </div>
</template>

<script>
import NetflixRatings from "./components/NetflixRatings.vue";

export default {
  name: "app",
  components: {
    NetflixRatings
  }
};
</script>

<style lang="scss">
@import "./styles/main.scss";

#app {
  margin-top: 60px;
}
</style>