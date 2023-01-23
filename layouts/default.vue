<template>
  <div class="l-main">
    <Header />
    <Nuxt />
    <div class="loader" v-if="isLoading">
      <div class="loader__case">
        <div class="loader__case_arrow"></div>
      </div>
      <div class="loader__text">loading...</div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Loader from "~/components/Loader";
import Header from "~/components/Header";
import Footer from "../components/Footer";

export default {
  name: "default",
  components: {
    Footer,
    Header,
    Loader,
  },
  data() {
    return {
      isLoading: false
    }
  },
  computed: {},
  methods: {}
}
</script>

<style lang="scss">
@import "assets/styles/global";

.l-main {
  min-height: 100vh;
  transition: all .3s;
  background-image:linear-gradient(to top, transparent 0,  rgba(0,0,0,0.9) 80%), url("./assets/images/secBackground.jpg");
  background-attachment: fixed;
  background-size: 100% 155%;
  background-position: center;
  background-repeat: no-repeat;
  @media screen and (max-width: 550px) {
    background-size: cover;
  }
}

.to-menu-arrow {
  position: absolute;
  left: 40px;
  top: 40px;
}
</style>
