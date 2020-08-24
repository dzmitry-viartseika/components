<template>
  <aside class="admin-left-sidebar">
    >
      <div class="admin-left-sidebar__top">
        <div
          class="admin-left-sidebar__logo"
          @click="goToPage('country')"
        >
        </div>
        <div class="admin-left-sidebar-menu">
          <div
            v-for="(item) in sidebarMenu"
            :key="item.id"
            class="admin-left-sidebar-menu__item"
            :class="{'admin-left-sidebar-menu__item_active': activeMenuItem === item.route}"
            @click="goToPage(item.route)"
          >
            <i
              :class="`ub-icon-${item.route}`"
            >
            </i>
            <span>
              {{ item.name }}
            </span>
            <div v-if="item.sub" class="list">
              <div v-for="el in item.sub" :key="el.id">
                {{ el.name }}
              </div>
            </div>
          </div>
        </div>
      </div>
  </aside>
</template>

<script>

export default {
  name: 'LeftSidebar',
  data() {
    return {
      activeMenuItem: '',
      loader: false,
    };
  },
  computed: {
    sidebarMenu() {
      return [
        {
          id: 1,
          name: '1',
          route: 'country',
        },
        {
          id: 2,
          name: '2',
          route: 'partners',
        },
        {
          id: 3,
          name: '3',
          route: 'services',
        },
        {
          id: 4,
          name: '4',
          route: 'staff',
        },
        {
          id: 5,
          name: '5',
          route: 'clients',
        },
        {
          id: 6,
          name: '6',
          route: 'reports',
        },
        {
          id: 7,
          name: '7',
          route: 'settings',
          sub: [
            {
              id: 1,
              name: '11',
              route: 'settings',
            },
            {
              id: 2,
              name: '111',
              route: 'settings',
            },
          ],
        },
      ];
    },
    userInfo() {
      return this.$store.getters.userInfo;
    },
    fullName() {
      return `${this.userInfo.firstName || ''} ${this.userInfo.lastName || ''}`;
    },
  },
  methods: {
    goToPage(page) {
      this.$router.push({
        name: page,
      });
      this.activeMenuItem = page;
    },
    logOut() {
      localStorage.removeItem('token');
      localStorage.removeItem('rememberMe');
      this.goToPage('loginPage');
    },
  },
};

</script>

<style scoped lang="scss">
  @import "../sass/variables";

  .admin-left-sidebar {
    display: flex;
    flex-direction: column;
    min-width: 240px;
    max-width: 240px;
    background: $color-white;
    height: 100vh;
    padding: 21px 0 0;
    justify-content: space-between;

    &__scroll {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      height: 100vh;
    }

    &__logo {
      margin-left: 25px;
      margin-bottom: 20px;
      cursor: pointer;
      max-width: 163px;
      width: 100%;
    }

    &-menu {
      display: flex;
      flex-direction: column;

      &__item {
        height: 46px;
        display: flex;
        align-items: center;
        padding: 0 25px;
        position: relative;
        cursor: pointer;
        transition: background-color .15s ease-in;

        & + .admin-left-sidebar-menu__item {
          margin-top: 5px;
        }

        &:before {
          content: '';
          position: absolute;
          top: 0;
          left: 0;
          height: 100%;
          border-radius: 0 $borderRadius $borderRadius 0;
          background: $color-dodger-blue;
          width: 4px;
          opacity: 0;
          transition: .15s ease-in;
        }

        i {
          margin-right: 10px;
          color: $color-silver-chalice;
          transition: color .15s ease-in;
        }

        span {
          color: $color-silver-chalice;
          text-decoration: none;
          transition: color .15s ease-in;
        }

        &_active {
          background: rgba($color-dodger-blue, .08);

          span, i {
            color: $color-dodger-blue;
          }

          span {
            font-family: $font-global-medium;
          }

          &:before {
            opacity: 1;
          }
        }

        &:hover {
          span, i {
            color: $color-dodger-blue;
          }
        }
      }
    }
  }

  .logout {
    color: $color-silver-chalice;
    min-height: 74px;
    max-height: 74px;
    border-top: 1px solid $color-alabaster;
    display: flex;
    align-items: center;
    margin-top: 25px;

    &__content {
      height: 46px;
      display: flex;
      flex-grow: 1;
      align-items: center;
      padding: 0 25px;
      position: relative;
      cursor: pointer;
      transition: background-color .15s ease-in;

      i {
        margin-right: 10px;
        color: $color-silver-chalice;
        transition: color .15s ease-in;
      }

      span {
        color: $color-silver-chalice;
        text-decoration: none;
        transition: color .15s ease-in;
      }

      &:hover, &_active {

        span, i {
          color: $color-dodger-blue;
        }

        span {
          font-family: $font-global-medium;
        }

        &:before {
          opacity: 1;
        }
      }
    }

    &__icon {
      font-size: $font-size-h2;
      color: $color-silver-chalice;
      margin-right: 10px;
    }

    &__text {
      cursor: pointer;
    }
  }

  .account {
    margin-top: 15px;
    padding: 0 25px;
    display: flex;
    align-items: center;
    transition: opacity .15s ease-in;

    &__content {
      display: flex;
      align-items: center;
      transition: opacity .15s ease-in;
      cursor: pointer;

      &:hover {
        opacity: .7;
      }
    }

    &__name {
      font-family: $font-global-medium;
    }

    &__image {
      width: 32px;
      height: 32px;
      background: $color-dodger-blue;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 12px;

      i {
        color: $color-white;
        font-size: 22px;
      }
    }
  }

  .admin-left-sidebar-menu__item:last-child {
    height: 96px;
    display: flex;
    align-items: flex-start;
  }

  .list {
    display: flex;
    flex-direction: column;
    margin-top: 30px;
  }

</style>
