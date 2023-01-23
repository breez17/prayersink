<template>
  <div class="loader">
    <div class="loader__case">
      <div class="loader__case_arrow"></div>
    </div>
    <div class="loader__text">loading...</div>
  </div>
</template>

<script>
export default {
  name: "Loader"
}
</script>

<style lang="scss">
.loader {
  //display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  z-index: 50;

  &__case {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    &_arrow {
      width: 80px;
      height: 80px;
      border-top: 3px solid #fff;
      border-bottom: 3px solid #fff;
      border-right: none;
      border-left: none;
      border-radius: 50px;
      animation: loader 1s linear infinite;
    }
  }

  &__text {
    position: fixed;
    top: 50%;
    left: 50%;
    width: 100px;
    transform: translate(-50%, -50%);
    color: #fff;
    text-align: center;
    animation: loader-text 2s linear infinite;
  }
}

@keyframes loader {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

@keyframes loader-text {
  0% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
