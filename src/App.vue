<template>
  <div id="app">
    <HackerNews />
  </div>
</template>

<script>
import HackerNews from "./components/HackerNews.vue";

export default {
  name: "app",
  components: {
    HackerNews
  }
};
</script>

<style lang="scss">
@import "./styles/main.scss";

#app {
  margin-top: 60px;
}
</style>