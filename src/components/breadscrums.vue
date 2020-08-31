<template>
  <div class="ub-breadcrumb">
    <div
      v-for="(item, index) in items"
      :key="item.name"
      class="ub-breadcrumb__item"
      :class="{'ub-breadcrumb__item_active': index === items.length -1}"
      @click="index !== items.length -1 ? proceedTo(item.route) : false"
    >
      {{ item.name }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'BreadCrums',
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    proceedTo(route) {
      this.$router.push(route);
    },
  },
};
</script>

<style scoped lang="scss">
@import "../sass/variables";

.ub-breadcrumb {
  display: flex;
  margin-bottom: 16px;

  &__item {
    color: $color-silver-chalice;

    &_active {
      color: $color-dodger-blue;
    }
  }

  &__item + &__item {
    position: relative;
    margin-left: 17px;

    &:after {
      position: absolute;
      content: '/';
      left: -11px;
      top: 1px;
      color: $color-silver-chalice;
    }
  }
}
</style>
