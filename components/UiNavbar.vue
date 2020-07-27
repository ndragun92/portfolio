<template>
  <nav class="ui-navbar">
    <div class="g-container ui-navbar__container">
      <div class="ui-navbar__logo" @click="$router.push('/')">
        <img src="~static/images/avatar.png" alt="">
        <span>Nemanja <strong>Dragun</strong></span>
      </div>
      <ul class="ui-navbar__links">
        <li v-for="link in links" :key="link.href">
          <nuxt-link class="ui-navbar__link" :to="link.href" :class="{'ui-navbar__link--bordered': link.bordered}">
            <i v-if="link.icon" :class="[link.icon]" />{{ link.name }}
          </nuxt-link>
        </li>
        <li class="ui-navbar__link--theme">
          <a role="button" @click="toggleTheme()"><i
            class="fas"
            :class="themeToChose === 'dark' ? 'fa-moon' :
              'fa-sun'"
          /></a>
        </li>
        <li class="ui-navbar__link--theme">
          <a role="button" @click="accessibilityTheme()"><i class="fas fa-universal-access" /></a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  data: () => ({
    links: [
      {
        name: 'Home',
        href: '/',
        icon: 'fas fa-home'
      },
      {
        name: 'Recent work',
        href: '/recent-work'
      },
      {
        name: 'Tutorials',
        href: '/tutorials'
      },
      {
        name: 'Contact me',
        href: '/contact',
        bordered: true
      }
    ]
  }),
  computed: {
    themeToChose () {
      return this.$store.state.theme.palette === 'light' ? 'dark' : 'light'
    },
    themeToDelete () {
      return this.$store.state.theme.palette !== 'light' ? 'dark' : 'light'
    }
  },
  async mounted () {
    if (this.$cookies.get('theme')) {
      await this.$store.commit('theme/SET_THEME', this.$cookies.get('theme'))
      this.selectTheme()
    }
  },
  methods: {
    async toggleTheme () {
      await this.$store.commit('theme/SET_THEME', this.themeToChose)
      this.selectTheme()
    },
    selectTheme () {
      document.documentElement.classList.remove(`theme-${this.themeToChose}`)
      document.documentElement.classList.remove('theme-accessibility')
      document.documentElement.classList.add(`theme-${this.themeToDelete}`)
    },
    accessibilityTheme () {
      document.documentElement.classList.remove(`theme-${this.themeToChose}`)
      document.documentElement.classList.add('theme-accessibility')
    }
  }
}
</script>

<style lang="scss" scoped>
  .ui-navbar {
    top: 0;
    position: absolute;
    width: 100%;
    z-index: $z_index-fixed;
    height: 60px;
    &__container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      height: 80px;
    }
    &__logo {
      text-transform: uppercase;
      margin: 0;
      font-size: 18px;
      font-weight: 400;
      color: var(--always-text-light-primary);
      display: flex;
      align-items: center;
      img {
        $size: 35px;
        width: $size;
        height: $size;
        display: block;
      }
      span {
        margin-left: 10px;
      }
      strong {
        color: var(--active-color-primary);
      }
      @include upToSmallDesktop {
        background-color: red;
      }
    }
    &__links {
      list-style: none;
      padding: 0;
      margin: 0;
      li {
        display: inline-block;
        margin: 0 10px;
        a {
          padding: 5px 10px;
          cursor: pointer;
          font-size: 16px;
          color: var(--always-text-light-primary);
          text-decoration: none;
          text-transform: uppercase;
          i {
            margin-right: 10px;
          }
        }
      }
    }
    &__link {
      &:hover {
        -webkit-mask-image: linear-gradient(-75deg,rgba(0,0,0,.6) 30%,#000 50%,rgba(0,0,0,.6) 70%);
        -webkit-mask-size: 200%;
        -webkit-animation: shine-data 2s infinite;
        animation: shine-data 2s infinite
      }
      @-webkit-keyframes shine-data {
        0% {
          -webkit-mask-position: 150%
        }

        to {
          -webkit-mask-position: -50%
        }
      }
      &--bordered {
        border: 1px solid var(--active-color-primary);
      }
      &--theme {
        margin: 0 !important;
        i {
          margin: 0 !important;
        }
      }
    }

  }
</style>
