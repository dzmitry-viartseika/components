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
      <div class="cookies" v-if="!cookieToken">
        <div class="cookies-info">
          <div class="cookies__text">
            Мы используем cookie-файлы.
            Продолжая использовать сайт, вы соглашаетесь на работу с этими файлами.
            <a href="#" class="cookies__link">Что это значит?</a>
          </div>
        </div>
        <div class="cookies-btns">
          <button class="cookies-btns__btn cookies-btns__btn_border" @click="close">
            <span>Нет, спасибо</span>
          </button>
          <button class="cookies-btns__btn cookies-btns__btn_primary" @click="accept">
            <span>Окей</span>
          </button>
        </div>
      </div>
    <nav id="hf-nav">
      <div v-for="item in itemLinks" :key="item.link"
      >
        <a :href="`${item.link}`">{{ item.title }}</a>
        <nav v-if="item.subItems">
          <a v-for="sub in item.subItems" :key="sub.link"  :href="`${sub.link}`">{{ sub.title }}</a>
        </nav>
      </div>
    </nav>
  </div>
</template>

<script>
import dropdown from './components/elements/dropdown.vue';
import buttonComponent from './components/elements/buttonComponent.vue';

export default {
  name: 'App',
  components: {
    dropdown,
    myButton: buttonComponent,
  },
  data: () => ({
    itemLinks: [
      { title: 'Home', link: './' },
      {
        title: '1',
        link: './diensten',
        subItems: [
          { title: '2', link: './elektromontage' },
          { title: '3', link: './installatietechniek' },
          { title: '4', link: './schoonmaak' },
          { title: '5', link: './overige-diensten' },
        ],
      },
      { title: '6', link: './over-hf' },
      { title: '7', link: './contact' },
    ],
    cookieToken: false,
  }),
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
    close() {
      this.cookieToken = true;
      localStorage.setItem('cookie', false);
    },
    accept() {
      this.cookieToken = true;
      localStorage.setItem('cookie', true);
    },
    callback() {
      console.log('clicked button');
    },
  },
  beforeMount() {
    const token = JSON.parse(localStorage.getItem('cookie'));
    if (token) {
      this.cookieToken = true;
    } else {
      this.cookieToken = false;
    }
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
