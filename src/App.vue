<template>
  <div id="app">
    <photo-comment></photo-comment>
  </div>
</template>

<script>
import PhotoComment from "./components/PhotoComment.vue";

export default {
  name: "app",
  components: {
    PhotoComment
  }
};
</script>

<style lang="scss">
@import "./styles/main.scss";

#app {
  margin-top: 60px;
}
</style>