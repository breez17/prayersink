<template>
  <div class="home-page">
    <Loader v-if="isLoading" />
    <div class="container">
      <div class="home-page__wrapper">
        <div class="home-page__wrapper-designs">
          <div class="c-about__title">
            <h2 class="c-about__title-item headline-2"
                data-aos="fade-right"
                data-aos-easing="ease"
            >
              Designs
            </h2>
          </div>
            <div data-aos-duration="12000" data-aos="fade-up" v-swiper:mySwiper="options">
              <div class="swiper-wrapper">
                <div
                    v-for="image in images"
                    :key="image.id"
                    class="img-wrapper swiper-slide"
                    @click="zoomedImage = image"
                >
                  <img :src="image.url" alt="">
                </div>
              </div>
              <div class="swiper-next swiper-button-next"></div>
              <div class="swiper-prev swiper-button-prev"></div>
            </div>
        </div>
        <div class="home-page__wrapper-works">
          <div class="c-about__title">
            <h2 class="c-about__title-item headline-2"
                data-aos="fade-right"
                data-aos-easing="ease"
            >
              Gallery
            </h2>
          </div>
            <WorkSlider @setZoom="setZoom" data-aos-duration="12000" data-aos="fade-up" :options="workOptions" :works="works" />
        </div>
      </div>
      <About/>
      <Contact />
    </div>
    <ZoomedImage
        v-if="Object.keys(zoomedImage).length"
        :image="zoomedImage"
        @closeZoom="zoomedImage = {}"
    />
  </div>
</template>

<script>
import WorkSlider from "@/components/WorkSlider";
import ZoomedImage from "@/components/ZoomedImage";
import About from "@/components/About";
import Loader from "@/components/Loader";
import Contact from "@/components/Contact";
export default {
  name: 'IndexPage',
  components: {
    Contact,
    Loader,
    About,
    ZoomedImage,
    WorkSlider
  },
  layout: "default",
  data() {
    return {
      isLoading: false,
      zoomedImage: {},
      isViewSlides: false,
      options: {
        slidesPerView: 1.8,
        slidesPerGroup: 1,
        initialSlide: 1,
        spaceBetween: 0,
        centeredSlides: true,
        loopedSlides: 2,
        autoplay: {
          delay: 500
        },
        speed: 1000,
        loop: true,
        navigation: {
          nextEl: '.swiper-next',
          prevEl: '.swiper-prev',
        },
      },
      workOptions: {
        breakpoints: {
          550: {
            slidesPerView: 1.2,
          }
        },
        slidesPerView: 2.2,
        slidesPerGroup: 1,
        initialSlide: 2,
        loopedSlides: 2,
        spaceBetween: 0,
        centeredSlides: true,
        loop: true,

        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },
        speed: 1000
      },
      images: [],
      works: []
    }
  },
  methods: {
    setZoom(value) {
      this.zoomedImage = value
    },
  },
  async created() {
    this.isLoading = true;
    try {
      this.images = (await this.$fire.database.ref('/designs').get()).val()
      this.works = (await this.$fire.database.ref('/works').get()).val()
      setTimeout(() => {
        this.isViewSlides = true;
      },400)
      this.isLoading = false;
      clearTimeout()
    } catch (error) {
      console.log(error)
      this.isLoading = false;
    }
  }
}
</script>

<style lang="scss">
.home-page {
  margin-top: calc(100vh - 48%);
  @media screen and (max-width: 950px) {
    margin-top: 20px;
  }
  &__wrapper {
    display: flex;
    justify-content: space-between;
    gap: 50px;
    min-height: 450px;
    @media screen and (max-width: 1150px) {
      flex-direction: column;
    }
    &-designs {
      width: 45%;
      @media screen and (max-width: 1150px) {
        margin: 0 auto;
        width: 100%;
      }
    }
    &-works {
      width: 45%;
      @media screen and (max-width: 1150px) {
        margin: 0 auto;
        width: 100%;
      }
    }
  }
}
.swiper-slide {
  height: 400px;
  cursor: grab;
  transition: all 0.3s;
  border-radius: 4px;
  @media screen and (max-width: 1150px) {
    height: 500px;
  }
  @media screen and (max-width: 920px) {
    height: 400px;
  }
  img {
    width: 100%;
    height: 100%;
    border-radius: 4px;
    object-fit: cover;
  }
  &-prev {
    opacity: .9;
    scale: 0.9;
  }
  &-next {
    opacity: .9;
    scale: 0.9;
  }
}
.swiper-prev {
  background-image: url('../assets/icons/arrow-left.svg');
  position: absolute;
  width: 36px;
  height: 36px;
  top: 50%;
  cursor: pointer;
  left: 0;
}
.swiper-next {
  background-image: url('../assets/icons/arrow-right.svg');
  right: 0;
  position: absolute;
  width: 36px;
  height: 36px;
  top: 50%;
  cursor: pointer;
}

</style>
