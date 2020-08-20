<template>
  <div id="app">
    <div>
      <h2>Dropdown</h2>
      <dropdown :dropdownOptions="dropdownOptions"/>
    </div>
    <div>
      <h2>Button</h2>
      <my-button :buttonOptions="buttonOptions"/>
    </div>
    <cookie-law>
      <div slot-scope="props" class="cookies">
        <div class="cookies-info">
          <div class="cookies__text">
            Мы используем cookie-файлы.
            Продолжая использовать сайт, вы соглашаетесь на работу с этими файлами.
            <a href="#" class="cookies__link">Что это значит?</a>
          </div>
        </div>
        <div class="cookies-btns">
          <button class="cookies-btns__btn cookies-btns__btn_border" @click="props.close">
            <span>Нет, спасибо</span>
          </button>
          <button class="cookies-btns__btn cookies-btns__btn_primary" @click="props.accept">
            <span>Окей</span>
          </button>
        </div>
      </div>
    </cookie-law>
  </div>
</template>

<script>
import CookieLaw from 'vue-cookie-law';
import dropdown from './components/elements/dropdown.vue';
import buttonComponent from './components/elements/buttonComponent.vue';

export default {
  name: 'App',
  components: {
    dropdown,
    myButton: buttonComponent,
    CookieLaw,
  },
  computed: {
    dropdownOptions() {
      return {
        list: [
          {
            code: 'Ru',
            text: 'Russian',
          },
          {
            code: 'En',
            text: 'English',
          },
        ],
      };
    },
    buttonOptions() {
      return {
        type: 'success',
        buttonText: 'Click me',
        disabled: false,
        event: this.callback(),
        icon: 'test',
      };
    },
  },
  methods: {
    callback() {
      console.log('clicked button');
    },
  },
};
</script>

<style lang="scss">
  @import "sass/core";

  .test {
    width: 50px;
    height: 50px;
    background: red;
    margin: 0 15px;
  }

  .vueperslides__track-inner {
    align-items: center;
  }

  .vueperslide.test.vueperslide--active.vueperslide--visible {
    background: green;
    width: 70px;
    height: 70px;
  }
</style>
