<template>
  <button class="button"
          :class="options.type"
          :disabled="options.disabled"
          @click="buttonOptions.onClick"
  >
    <i :class="`icon-${options.icon}`" v-if="options.icon" class="button__icon"></i>
    {{ options.buttonText }}
  </button>
</template>

<script>
export default {
  name: 'buttonComponent',
  props: {
    buttonOptions: {
      type: Object,
      default: () => {},
    },
  },
  computed: {
    options() {
      return this.buttonOptions;
    },
  },
  methods: {
    test2() {
      this.$emit('buttonOptions.onClick');
    },
  },
  beforeMount() {
    console.log('buttonOptions', this.buttonOptions);
  },
};
</script>

<style scoped lang="scss">
  @import "src/sass/variables";

  .button {

    &__icon {
      margin-right: 5px;
    }
  }
</style>
