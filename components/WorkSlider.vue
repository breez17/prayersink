<template>
  <div v-swiper:mySwiper="options">
    <div class="swiper-wrapper">
      <div
          v-for="work in works"
          @click="$emit('setZoom', work)"
          :key="work.id"
          class="img-wrapper swiper-slide"
      >
        <img :src="work.url" alt="">
      </div>
    </div>
    <div class="swiper-next swiper-button-next"></div>
    <div class="swiper-prev swiper-button-prev"></div>
  </div>
</template>

<script>
import ZoomedImage from "./ZoomedImage";
export default {
  name: "WorkSlider",
  components: {ZoomedImage},
  props: {
    options: {
      type: Object,
      default: []
    },
    works: {
      type: Object | Array,
      default: []
    }
  },
}
</script>

<style scoped>

</style>
