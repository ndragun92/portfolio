<template>
  <nav class="ui-navbar">
    <div class="ui-navbar__container">
      <div class="ui-navbar__logo">
        <span>Nemanja <strong>Dragun</strong></span>
      </div>
      <ul class="ui-navbar__links">
        <li v-for="link in links" :key="link.href">
          <nuxt-link :to="link.href">
            {{ link.name }}
          </nuxt-link>
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
        href: '/'
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
        href: '/contact'
      }
    ]
  })
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
      width: 100%;
      max-width: 1200px;
      padding: 0 20px;
      margin: auto;
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
      color: var(--light-text-primary-color);
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
        margin: 0 20px;
        a {
          font-size: 16px;
          color: var(--light-text-primary-color);
          text-decoration: none;
          text-transform: uppercase;
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
        }
      }
    }
  }
</style>
