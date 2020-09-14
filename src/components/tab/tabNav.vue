<template>
  <div class="ub-tab">
      <div class="ub-tab-nav">
        <div class="ub-tab-nav__item" v-for="tab in tabs" :key="tab" @click="setTab(tab)">
          {{ tab }}
        </div>
      </div>
    <slot></slot>
  </div>
</template>

<script>

export default {
  name: 'tabNav',
  props: {
    tabs: {
      type: Array,
      default: () => [],
      required: true,
    },
    selected: {
      type: String,
      default: () => '',
      required: true,
    },
  },
  methods: {
    setTab(activeTab) {
      console.log('activeTab', activeTab);
      this.$emit('selected', activeTab);
    },
  },
};
</script>

<style scoped lang="scss">
@import "../../sass/variables";

  .ub-tab-nav {
    width: 30%;
  }
</style>
