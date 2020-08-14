<template>
  <button class="normal"
          :class="options.type"
          :disabled="options.disabled"
          @click="callback($event)"
  >
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
    callback(e) {
      this.$emit('options.event', e);
    },
  },
};
</script>

<style scoped lang="scss">
  @import "src/sass/variables";

  .button {

  }
</style>
