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
    <vueper-slides
      :visible-slides="9"
      :arrows="false"
      :bullets="false"
      :dragging-distance="70">
      <vueper-slide class="test" v-for="i in 12" :key="i.img" :title="i" />
    </vueper-slides>
  </div>
</template>

<script>
import { VueperSlides, VueperSlide } from 'vueperslides';
import dropdown from './components/elements/dropdown.vue';
import buttonComponent from './components/elements/buttonComponent.vue';

export default {
  name: 'App',
  components: {
    dropdown,
    myButton: buttonComponent,
    VueperSlides,
    VueperSlide,
  },
  data: () => ({
    sliders: [
      {
        id: 1,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTwrjdzos2b12kN2KOEwz0kTuVFGtGR9bvHTg&usqp=CAU',
      },
      {
        id: 2,
        img: 'data:image/jpeg;base64,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',
      },
      {
        id: 3,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTwrjdzos2b12kN2KOEwz0kTuVFGtGR9bvHTg&usqp=CAU',
      },
      {
        id: 4,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQkAkjDjkJ5Zpr_Pe6wr2O2028hHUXc1B-ASw&usqp=CAU',
      },
      {
        id: 5,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTwrjdzos2b12kN2KOEwz0kTuVFGtGR9bvHTg&usqp=CAU',
      },
      {
        id: 6,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTwrjdzos2b12kN2KOEwz0kTuVFGtGR9bvHTg&usqp=CAU',
      },
      {
        id: 7,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTwrjdzos2b12kN2KOEwz0kTuVFGtGR9bvHTg&usqp=CAU',
      },
      {
        id: 8,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTwrjdzos2b12kN2KOEwz0kTuVFGtGR9bvHTg&usqp=CAU',
      },
      {
        id: 9,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTwrjdzos2b12kN2KOEwz0kTuVFGtGR9bvHTg&usqp=CAU',
      },
      {
        id: 10,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTwrjdzos2b12kN2KOEwz0kTuVFGtGR9bvHTg&usqp=CAU',
      },
    ],
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
