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

<style>
  @import '../node_modules/vueperslides/dist/vueperslides.css';
</style>

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
