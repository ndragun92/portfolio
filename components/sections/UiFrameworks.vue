<template>
  <section class="ui-frameworks">
    <div class="g-container">
      <h2 class="h2">
        Things that i know - <button @click="frontend">
          Frontend
        </button>
        <button @click="backend">
          Backend
        </button>
        <button @click="other">
          Other
        </button>
      </h2>
      <div class="heading__separator" />
      <transition-group tag="ul" class="ui-frameworks__list" name="ui-frameworks__list--animation">
        <li
          v-for="item in list"
          :key="item"
          class="ui-frameworks__list-item"
          :class="{ active: selectedList.includes(item) }"
        >
          <img :src="`http://nemanja-portfolio.herokuapp.com/images/frameworks/${item}.jpg`" alt="">
        </li>
      </transition-group>
    </div>
  </section>
</template>

<script>
import shuffle from 'lodash/shuffle'
const defaultList = ['adonis', 'angular', 'bootstrap', 'feathers',
  'css', 'git', 'html', 'intellij', 'js', 'laravel',
  'mongodb', 'mysql', 'nuxt', 'photoshop', 'php', 'sass',
  'vue', 'vuetify']
export default {
  data: () => ({
    list: defaultList,
    selectedList: []
  }),
  methods: {
    frontend () {
      this.selectedList = ['nuxt', 'vue', 'angular', 'html', 'js', 'sass', 'css', 'bootstrap', 'vuetify']
      this.list = [...new Set([...this.selectedList, ...this.list])]
    },
    backend () {
      this.selectedList = ['adonis', 'feathers', 'laravel', 'php', 'mysql', 'mongodb']
      this.list = [...new Set([...this.selectedList, ...this.list])]
    },
    other () {
      this.selectedList = ['git', 'photoshop', 'intellij']
      this.list = [...new Set([...this.selectedList, ...this.list])]
    },
    all () {
      this.selectedList = []
      this.list = shuffle(defaultList)
    }
  }
}
</script>

<style lang="scss" scoped>
  .ui-frameworks {
    padding-top: 100px;
    padding-bottom: 60px;
    background-color: var(--light-secondary-color);
    clip-path: polygon(0% 100%, 0% 10%, 50% 0%, 100% 10%, 100% 100%);
    min-height: 500px;
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
      position: relative;
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
      &--animation {
        &-enter, &-leave-to {
          opacity: 0;
          transform: translateY(30px);
        }
        &-leave-active {
          position: absolute;
        }
      }
      &-item {
        transition: all 1s;
        border: 2px solid transparent;
        &.active {
          border-color: var(--active-color-primary)
        }
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
