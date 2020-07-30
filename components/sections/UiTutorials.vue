<template>
  <section class="ui-tutorials">
    <div class="g-container">
      Tutorials
    </div>
  </section>
</template>

<script>
export default {
  async fetch () {
    this.projects = await this.$content('projects').fetch()
  },
  data: () => ({
    projects: []
  })
}
</script>

<style lang="scss" scoped>
.ui-tutorials {
  padding: 40px 0 60px 0;
  min-height: calc(100vh - 555px);
  background-color: var(--light-primary-color);
  color: var(--dark-text-primary-color);
  user-select: none;
  @include upToMobile {
    min-height: calc(100vh - 405px);
  }
}
</style>
