<template>
  <div class="c-zoomed-image">
    <div class="c-zoomed-image__wrapper">
      <img v-on-clickaway="closeZoom" class="c-zoomed-image__wrapper-img" :src="image.url" alt="">
    </div>
  </div>
</template>

<script>
import { mixin as clickaway } from 'vue-clickaway';

export default {
  name: "ZoomedImage",
  props: {
    image: {
      type: Object,
    }
  },
  mixins: [ clickaway ],
  methods: {
    closeZoom() {
      this.$emit('closeZoom')
    }
  }
}
</script>

<style lang="scss">
.c-zoomed-image {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  cursor: pointer;
  z-index: 50;
  &__wrapper {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    &-img {
      width: 800px;
      object-fit: contain;
      height: 800px;
      @media screen and (max-width: 950px) {
        width: 600px;
        height: auto;
      }
      @media screen and (max-width: 550px) {
        width: 350px;
      }
    }
  }
}
</style>
