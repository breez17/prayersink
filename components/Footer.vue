<template>
  <div class="c-footer">
    <div class="c-footer__wrapper container">
      <a href="#" class="text-center">
        <img style="width: 30px" class="c-header__logo-holder_item" src="~/assets/images/logo.png" alt="logo">
      </a>
      <div class="c-footer__wrapper-social">
        <a class="c-about__holder-info_link" href="https://www.instagram.com/prayersink/" target="_blank">
          <img class="c-about__holder-info_link--icon" src="../assets/icons/instagram.svg" alt="">
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer"
}
</script>

<style lang="scss">
.c-footer {
  min-height: 60px;
  background: rgba(0,0,0, .85);
  padding: 20px 0;
  &__wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    @media screen and (max-width: 650px) {
      justify-content: center;
      gap: 50px;
    }
  }
}
</style>
