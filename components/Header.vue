<template>
  <div class="c-header">
    <div class="c-header__logo-holder text-center">
      <img class="c-header__logo-holder_item" src="~/assets/images/logo.png" alt="logo">
    </div>
    <div class="c-header__title text-center">
      <h2
          data-aos="fade-right"
          data-aos-easing="ease"
          class="c-header__title-item"
      >
        Prayersink
      </h2>
      <h4
          data-aos="fade-left"
          data-aos-easing="ease"
          class="c-header__title-subtitle headline-4"
      >
        Timmy Hardy
      </h4>
    </div>
    <nav class="c-header__navigation mt-5">
      <a href="#about" class="c-header__navigation-item body-1">
        About
      </a>
      <a href="#" class="c-header__navigation-item body-1">
        Designs
      </a>
      <a href="#" class="c-header__navigation-item body-1">
        Gallery
      </a>
      <a href="#" class="c-header__navigation-item body-1">
        FAQ
      </a>
      <a href="#contact" class="c-header__navigation-item body-1">
        CONTACTS
      </a>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style lang="scss">
.c-header {
  &__logo-holder {
    padding: 15px 0;
    &_item {
      width: 55px;
      @media screen and (max-width: 550px) {
        width: 40px;
      }
    }
  }
  &__title {
    &-item {
      font-family: 'EvilSound';
      font-size: 32px;
      letter-spacing: 20px;
      color: #FFFFFF;
      @media screen and (max-width: 650px) {
        font-size: 24px;
      }
    }
    &-subtitle {
      color: #FFFFFF !important;
    }
  }
  &__navigation {
    display: flex;
    align-items: center;
    max-width: 50%;
    margin: 0 auto;
    justify-content: space-around;
    color: white;
    text-transform: uppercase;
    @media screen and (max-width: 850px) {
      max-width: 70%;
    }
    @media screen and (max-width: 650px) {
      max-width: 75%;
    }
    @media screen and (max-width: 650px) {
      display: none;
    }
    &-item {
      text-decoration: none;
      font-family: 'Montserrat-Bold' !important;
      box-shadow: inset 0 0 0 0 #895428;
      color: #895428;
      min-width: 50px;
      padding: 0 .25em;
      transition: color .3s ease-in-out, box-shadow .3s ease-in-out;
      border-radius: 5px;
      &:hover {
        box-shadow: inset 140px 0 0 0 #895428;
        color: white;
      }
    }
  }
}
</style>
