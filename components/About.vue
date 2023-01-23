<template>
  <div class="c-about" id="about">
    <div class="c-about__title">
      <h2 class="c-about__title-item headline-2"
          data-aos="fade-right"
          data-aos-easing="ease"
      >
        About
      </h2>
    </div>
    <div class="c-about__holder">
      <div class="c-about__holder-avatar">
        <img class="c-about__holder-avatar_image" src="../assets/images/profile-photo.jpg" alt="">
      </div>
      <div class="c-about__holder-info"
           data-aos="fade"
           data-aos-easing="ease">
        <p>I’m Timmy Hardy. I’m from Ukraine , from beautiful port city - Odessa.  I’m 27 y.o.
          I work in tattoo industry around 10 years, professional work as tattoo artist since 2015.
          I opened my own tattoo shop “ Tesla Tattoo “ in the historical centre of my city.
          I can work in different styles, but prefer my own style more.  Black and white “Horror and Graffic art” .
          You can order design for your future tattoo from me . For order you need to describe place where you wanna do tattoo ( arm, leg, back, chest and etc.).
          Also you need to describe your idea and after it I’ll be able to do special design for you.
          Here you can see some of my works, but I have more on my instagram page.  I will be very grateful if you’ll follow me and like my posts. Also you can write to me in instagram for making appointment.</p>
        <a class="c-about__holder-info_link" href="https://www.instagram.com/prayersink/" target="_blank">
          <img class="c-about__holder-info_link--icon" src="../assets/icons/instagram.svg" alt="">
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "About"
}
</script>

<style lang="scss">
.c-about {
  margin-top: 80px;
  padding-bottom: 80px;
  @media screen and (max-width: 950px) {
    padding-bottom: 40px;
  }
  &__title {
    margin: 20px auto;
    color: white;
    font-size: 24px;
    &-item {
      color: white;
      @media screen and (max-width: 650px) {
        font-size: 32px;
        transform: none !important;
      }
    }
  }
  &__holder {
    display: flex;
    gap: 40px;
    @media screen and (max-width: 950px) {
      flex-direction: column;
    }
    &-avatar {
      width: 50%;
      @media screen and (max-width: 950px) {
        margin: 0 auto;
      }
      @media screen and (max-width: 550px) {
        width: 100%;
      }
      &_image {
        width: 100%;
      }
    }
    &-info {
      width: 50%;
      color: #FFFFFF;
      font-size: 18px;
      word-spacing: 2px;
      line-height: 35px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      @media screen and (max-width: 1500px) {
        font-size: 14px;
        word-spacing: normal;
        line-height: 25px;
      }
      @media screen and (max-width: 950px) {
        width: 100%;
        align-items: center;
      }

      p {
        @media screen and (max-width: 550px) {
          max-height: 300px;
          overflow: auto;
          margin-bottom: 20px;
          &::-webkit-scrollbar {
            width: 0.3em;
          }

          &::-webkit-scrollbar-track {
            box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.8);
          }

          &::-webkit-scrollbar-thumb {
            background-color: white;
            outline: 1px solid slategrey;
            border-radius: 5px;
          }
        }
      }

      &_link {
        max-width: 50px;
        display: block;
       &--icon {
         width: 100%;
       }
      }
    }
  }
}
</style>
