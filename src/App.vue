<template>
  <div id="app">
    <Modal>
      <p>Goodbye ?</p>
      <p>Oh no, please. Can't we go back to page one and do it all over again ?</p>
      <span>- Winnie The Pooh</span>
    </Modal>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "app",
  components: {
    Modal
  }
};
</script>

<style lang="scss">
@import "./styles/main.scss";

#app {
  margin-top: 60px;
}
</style>