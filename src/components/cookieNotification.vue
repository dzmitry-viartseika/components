<template>
  <div class="cookies">
    <div class="cookies-info">
      <div class="cookies__text">
        Мы используем cookie-файлы.
        Продолжая использовать сайт, вы соглашаетесь на работу с этими файлами.
        <a href="#" class="cookies__link">Что это значит?</a>
      </div>
    </div>
    <div class="cookies-btns">
      <button class="cookies-btns__btn cookies-btns__btn_border" @click="close">
        <span>Нет, спасибо</span>
      </button>
      <button class="cookies-btns__btn cookies-btns__btn_primary" @click="accept">
        <span>Окей</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'cookieNotification',
  methods: {
    close() {
      this.$emit('update:cookieToken', true);
      localStorage.setItem('cookie', false);
    },
    accept() {
      this.$emit('update:cookieToken', true);
      localStorage.setItem('cookie', true);
    },
  },
};
</script>

<style scoped>

</style>
