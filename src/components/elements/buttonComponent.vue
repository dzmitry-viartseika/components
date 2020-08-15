<template>
  <button class="button"
          :class="options.type"
          :disabled="options.disabled"
          @click="callback($event)"
  >
    <i :class="`icon-${options.icon}`" class="button__icon">123</i>{{ options.buttonText }}
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
    callback(e) {
      this.$emit('options.event', e);
    },
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
