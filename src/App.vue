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
    <cookieNotification v-if="!cookieToken" :cookieToken.sync="cookieToken"/>
  </div>
</template>

<script>
import dropdown from './components/elements/dropdown.vue';
import cookieNotification from './components/cookieNotification.vue';
import buttonComponent from './components/elements/buttonComponent.vue';

export default {
  name: 'App',
  components: {
    dropdown,
    cookieNotification,
    myButton: buttonComponent,
  },
  data: () => ({
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
        onClick: this.test,
        icon: 'test',
      };
    },
  },
  methods: {
    test() {
      console.log('clicked button');
    },
  },
  beforeMount() {
    const cookie = JSON.parse(localStorage.getItem('cookie'));
    if (cookie) {
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
