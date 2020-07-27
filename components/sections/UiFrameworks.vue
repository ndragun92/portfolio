<template>
  <section class="ui-frameworks">
    <div class="g-container">
      <h2 class="h2">
        Things that i know
      </h2>
      <div class="heading__separator" />
      <ul class="ui-frameworks__list">
        <li
          v-for="item in ['adonis', 'angular', 'bootstrap', 'feathers',
                          'css', 'git', 'html', 'intellij', 'js', 'laravel', 'mongodb', 'mysql', 'nuxt', 'photoshop', 'php', 'sass', 'vue', 'vuetify']"
          :key="item"
        >
          <img :src="`http://nemanja-portfolio.herokuapp.com/images/frameworks/${item}.jpg`" alt="">
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  data: () => ({
    list: []
  })
}
</script>

<style lang="scss" scoped>
  .ui-frameworks {
    padding-top: 100px;
    padding-bottom: 60px;
    background-color: var(--light-secondary-color);
    clip-path: polygon(0% 100%, 0% 10%, 50% 0%, 100% 10%, 100% 100%);
    @include upToTablet {
      padding-top: 80px;
      padding-bottom: 40px;
      clip-path: polygon(0% 100%, 0% 5%, 50% 0%, 100% 5%, 100% 100%);
    }
    @include upToMobile {
      padding-top: 40px;
      clip-path: none
    }
    &__list {
      padding: 0;
      list-style: none;
      margin: 0;
      display: grid;
      grid-template-columns: repeat(6, 1fr);
      grid-gap: 20px;
      @include upToSmallDesktop {
        grid-template-columns: repeat(5, 1fr);
      }
      @include upToTablet {
        grid-template-columns: repeat(4, 1fr);
      }
      @include upToMobile {
        grid-template-columns: repeat(3, 1fr);
        grid-gap: 10px;
      }
      @include smallMobile {
        grid-template-columns: repeat(2, 1fr);
      }
      img {
        display: block;
        width: 100%;
      }
    }
  }
  h2 {
    text-align: center;
    text-transform: uppercase;
    margin: 0;
    color: var(--dark-text-primary-color);
  }
</style>
