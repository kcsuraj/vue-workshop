<template>
  <div class="container">
    <div class="card">
      <p>Are you awesome ?</p>
      <br />
      <button class="btn">Yes</button>
    </div>

    <div class="modal" :class="{ active: isModalActive}">
      <span class="modal__close"></span>
      <div class="modal__content"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal"
};
</script>

<style scoped lang="scss">
.container {
  margin: 0 auto;
  max-width: 768px;
}

.card {
  box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
  padding: 24px;
}

.modal {
  background-color: rgba(#0e1724, 0.7);
  visibility: hidden;
  opacity: 0;
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  z-index: 999;

  &.active {
    visibility: visible;
    opacity: 1;
  }

  &__content {
    background-color: #fff;
    width: 50%;
    padding: 18px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate3d(-50%, -50%, 0);

    p {
      margin-bottom: 12px;
    }

    span {
      color: rgba(#3b4242, 0.7);
    }
  }

  &__close {
    background-color: #252e3b;
    display: block;
    height: 34px;
    width: 34px;
    position: absolute;
    top: 20px;
    right: 20px;
    opacity: 0.8;
    cursor: pointer;
    border: 2px solid #ecc417;
    border-radius: 50%;

    &:before,
    &:after {
      content: "";
      height: 16px;
      width: 2px;
      position: absolute;
      top: 50%;
      left: 50%;
      background: rgb(236, 196, 23);
      border-radius: 6px;
    }

    &:before {
      transform: translate(-50%, -50%) rotate(-45deg);
    }

    &:after {
      transform: translate(-50%, -50%) rotate(45deg);
    }
  }

  &--visible {
    opacity: 1;
    visibility: visible;
  }
}

.btn {
  color: #fff;
  cursor: pointer;
  background-color: #007bff;
  border-color: #007bff;
  padding: 6px 12px;
  border-radius: 6px;
  transition: all 0.1s ease-in;
  &:hover {
    background-color: #0069d9;
    border-color: #0062cc;
  }
}
</style>
