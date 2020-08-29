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
    <accordion  :items="items"/>
    <textInput
      :typeInput="'text'"
      :autofocus="true"
      :value.sync="newTypeService"
      @test="test"
    ></textInput>
  </div>
</template>

<script>
import dropdown from './components/elements/dropdown.vue';
import accordion from './components/elements/accordion.vue';
import textInput from './components/elements/textInput.vue';
import cookieNotification from './components/cookieNotification.vue';
import buttonComponent from './components/elements/buttonComponent.vue';

export default {
  name: 'App',
  components: {
    dropdown,
    cookieNotification,
    textInput,
    accordion,
    myButton: buttonComponent,
  },
  data: () => ({
    newTypeService: '',
    cookieToken: false,
    items: [{
      id: 1,
      title: 'Competition law',
      content: 'wer 1Schärer Attorneys at Law advises and represents you on questions of unfair competition and the anti-trust law, for example, for company mergers, anti-trust investigations and for the drafting of distribution agreements.',
    }, {
      id: 2,
      title: 'Constitutional, community and administrative law',
      content: 'test 2 Civil law regulates privities of contract between private persons, communities of persons and corporations. On the other hand, constitutional, community and administrative law is concerned with the legal relationship between a private person and the community sector (federation, cantons, communities, associations of communities), or amongst communities. The specialists at Schärer Attorneys at Law act as advisers and consultants for private persons as well as communities, and represent them in the legal proceedings of objection and appeal.',
    },
    {
      id: 3,
      title: 'Construction, planning and environmental law',
      content: 'greee 3Our specialists in the fields of construction, planning and environmental law advise and represent builders, planners and architects, corporations, affected neighboring communities and associations of communities in:',
    }],
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
