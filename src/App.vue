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

</style>
