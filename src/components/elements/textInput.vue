<template>
  <div
    class="text-field"
    :class="customClass"
    @click.stop
  >
    <div
      v-if="labelText"
      class="text-field__label"
    >
      {{ labelText }}
    </div>
    <div
      class="text-field-wrapper"
      :class="{'text-field-wrapper_error': errorStatus}"
    >
      <input
        ref="input"
        v-model="model"
        :type="typeInput"
        class="text-field__input"
        :autofocus="autofocus"
        :placeholder="placeholderText"
        :value="value"
        :class="{'text-field__input_padding': icon || clearButton}"
        @focus="inputFocusStatus(true)"
        @blur="inputFocusStatus(false)"
        @keydown="handleEventClick($event)"
      >
      <div
        v-if="clearButton"
        class="text-field-wrapper__circle"
        @click="clearText()"
      >
        <i
          class="ub-icon-close"
        ></i>
      </div>
      <i
        v-if="icon && model.length && !errorStatus"
        class="text-field__icon"
        :class="icon"
        @click="handleClickIcon()"
      ></i>
      <i
        v-if="icon && typeInput === 'text' && model.length && !errorStatus"
        class="ub-icon-eye-hidden text-field__icon"
        @click="handleClickIcon"
      ></i>
      <i
        v-if="errorStatus"
        class="ub-icon-info-valid text-field__icon text-field__icon_error"
      ></i>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TextInput',
  props: {
    clearButton: {
      type: Boolean,
      default: () => false,
    },
    labelText: {
      type: String,
      default: () => '',
    },
    typeInput: {
      type: String,
      default: () => '',
    },
    customClass: {
      type: String,
      default: () => '',
    },
    placeholderText: {
      type: String,
      default: () => '',
    },
    autofocus: {
      type: Boolean,
      default: () => false,
    },
    value: {
      type: String,
      default: () => '',
    },
    icon: {
      type: String,
      default: () => '',
    },
    errorStatus: {
      type: Boolean,
      default: () => false,
    },
  },
  computed: {
    model: {
      get() {
        return this.value;
      },
      set(data) {
        this.$emit('update:value', data);
      },
    },
  },
  mounted() {
    if (this.$refs !== undefined) {
      if (this.autofocus) {
        this.$refs.input.focus();
      }
    }
  },
  methods: {
    inputFocusStatus(e) {
      this.$emit('inputFocusStatus', e);
    },
    clearText() {
      this.$emit('clearInputValue');
      this.model = '';
    },
    handleClickIcon() {
      this.$emit('handleClickIcon');
    },
    handleEventClick(e) {
      if (e.keyCode === 13) {
        this.$emit('handleEventClick');
      } else {
        this.$emit('changeInput');
      }
    },
  },
};
</script>

<style scoped lang="scss">
  @import "../../sass/variables";

  .text-field {

    &_medium {
      input {
        font-family: $font-global-medium;
      }
    }

    &_364 {
      min-width: 364px;
      max-width: 364px;
    }

    &_200 {
      min-width: 200px;
      max-width: 200px;
    }

    &-wrapper {
      position: relative;

      &__circle {
        width: 20px;
        height: 20px;
        background: rgba($color-dodger-blue, .08);
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
        position: absolute;
        top: 11px;
        right: 12px;
        cursor: pointer;
        transition: opacity .15s ease-in;

        &:hover {
          opacity: .8;
        }

        i {
          color: $color-dodger-blue;
          font-size: 7px;
        }
      }

      &_error {

        .text-field__input {
          border: 1px solid $color-cardinal!important;
        }
      }
    }

    &__icon {
      position: absolute;
      right: 12px;
      top: 50%;
      color: $color-silver-chalice;
      transition: color .15s ease-in;
      cursor: pointer;
      transform: translateY(-50%);

      &_error {
        pointer-events: none;
        color: $color-cardinal!important;
      }

      &:hover {
        color: $color-dodger-blue;
      }
    }

    &__input {
      border: 1px solid $color-gallery;
      border-radius: $borderRadius;
      width: 100%;
      height: 40px;
      padding: 12px;
      font: $font-size-base $font-global;
      line-height: 1.42 ;
      transition: border-color .15s ease-in;

      &_padding {
        padding-right: 35px;
      }

      &:focus {
        border-color: $color-dodger-blue;
      }
    }

    &__label {
      color: $color-silver-chalice;
      font: $font-size-md $font-global-medium;
      line-height: 1.55;
      margin-bottom: 5px;
    }
  }
</style>
