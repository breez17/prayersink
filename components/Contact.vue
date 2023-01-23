<template>
  <div class="c-contact" id="contact">
    <div class="c-contact__title text-center">
      <h2 class="c-about__title-item headline-2"
          data-aos="fade-right"
          data-aos-easing="ease"
      >
        Contact
      </h2>
    </div>
    <form
        class="c-contact__form mt-5"
        data-aos="fade-left"
        data-aos-easing="ease"
        @submit.prevent="sendToTelegram"
    >
      <input
          v-model="data.name"
          placeholder="Name"
          required
          class="c-contact__form_input"
          type="text"
      />
      <input
          v-model="data.email"
          placeholder="Email"
          required
          class="c-contact__form_input"
          :class="{'c-contact__form_input--error': !isValidEmail(this.data.email) && this.data.email !== ''}"
          type="text"
      />
      <span v-if="!isValidEmail(this.data.email) && this.data.email !== ''" class="c-contact__form_error-message">
        Email address is invalid!
      </span>
      <input
          v-model="data.subject"
          placeholder="Subject"
          class="c-contact__form_input"
          type="text"
      />
      <textarea
          v-model="data.message"
          required
          placeholder="Message..."
          class="c-contact__form_ta"
      />
      <button class="c-contact__form-button mt-5" type="submit">
        Submit
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Contact",
  data() {
    return {
      uuid: '5748892946:AAHEZ7dO1gWYuOXWLRgaokHlTDCbCO_r1as',
      chatID: '-1001840889592',
      data: {
        name: '',
        email: '',
        subject: '',
        message: ''
      },
    }
  },
  methods: {
    clearData() {
      this.data = {
        name: '',
        email: '',
        subject: '',
        message: ''
      }
    },
    isValidEmail(value) {
      return /^[A-Z0-9._%+-]+@[A-Z0-9-]+.+.[A-Z]{2,4}$/i.test(value)
    },
    async sendToTelegram () {
      if (this.isValidEmail(this.data.email)) {
        try {
          await fetch(`https://api.telegram.org/bot${this.uuid}/sendMessage?chat_id=${this.chatID}&parse_mode=HTML&text=%F0%9F%92%AA%20New%20Message%21%21%21%0A%F0%9F%91%B9%20From%3A%20${this.data.name}%0A%E2%9C%89%EF%B8%8F%20Email%3A%20${this.data.email}%0A%F0%9F%93%9D%20Subject%3A%20${this.data.subject}%0A%20%F0%9F%90%BE%20Message%3A%20${this.data.message}`, {
            method: 'GET',
          });
          this.$toasted.success('The Message has been sent!', {
            duration: 3000
          })
        } catch (error) {
          console.log(error);
          this.$toasted.error('Sorry, something went wrong, please contact by Instagram!',{
            duration: 3000
          })
        }
        this.clearData();
      }
    }
  },
}
</script>

<style lang="scss">
.c-contact {
  @media screen and (max-width: 650px) {
    overflow: hidden;
  }
  &__form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding-bottom: 30px;
    max-width: 50%;
    margin: 0 auto;
    border-radius: 4px;
    @media screen and (max-width: 950px) {
      max-width: 70%;
    }
    @media screen and (max-width: 650px) {
      max-width: 90%;
      transform: none !important;
    }
    &_input {
      height: 40px;
      border: none;
      border-bottom: 2px solid white;
      padding-left: 15px;
      outline: none;
      background: rgba(0,0,0, .4);
      color: white;
      @media screen and (max-width: 550px) {
        height: 35px;
      }
      &::placeholder {
        color: #FFFFFF;
      }
      &--error {
        border-color: red;
        color: red;
      }
    }
    &_ta {
      height: 120px;
      background: rgba(0,0,0, .4);
      border: none;
      border-bottom: 2px solid white;
      padding-left: 15px;
      outline: none;
      resize: none;
      color: white;
      &::placeholder {
        color: #FFFFFF;
      }
      &--error {
        border-color: red;
        color: red;
      }
    }
    &-button {
      border: 1px solid white;
      height: 40px;
      width: 200px;
      background: none;
      color: white;
      transition: all 0.3s;
      cursor: pointer;
      border-radius: 10px;
      &:hover {
        background: white;
        color: black;
      }
      @media screen and (max-width: 550px) {
        height: 35px;
        width: 150px;
      }
    }
    &_error-message {
      color: red;
      font-size: 10px;
      font-family: 'Montserrat-Bold';
    }
  }
}
</style>
