<template>
  <div class="ui-frameworks">
    <section class="g-container">
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
    </section>
  </div>
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
    &__list {
      padding: 0;
      list-style: none;
      margin: 0;
      display: grid;
      grid-template-columns: repeat(6, 1fr);
      grid-gap: 20px;
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
