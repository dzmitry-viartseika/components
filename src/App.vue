<template>
  <div id="app">
    <h1>Components</h1>
    <dropdown :dropdownOptions="dropdownOptions"/>
  </div>
</template>

<script>
import dropdown from './components/elements/dropdown.vue';

export default {
  name: 'App',
  components: {
    dropdown,
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
  },
};
</script>

<style lang="scss">
  @import "sass/core";

</style>
