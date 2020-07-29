<template>
  <section class="ui-projects">
    <div class="g-container">
      <div class="ui-projects__cards">
        <div
          v-for="(project, index) in projects"
          :key="index"
          class="ui-projects__card"
        >
          <img :src="`images/screenshots/${project.screenshot}.jpg`" alt="">
          <div class="ui-projects__card-box">
            <div class="ui-projects__card-box__name">
              {{ project.title }}
            </div>
            <div class="ui-projects__card-box__tech">
              <img v-for="tech in project.tech" :key="`${tech.image}_${index}`" :src="`images/frameworks/${tech.image}.jpg`" :alt="tech.name">
            </div>
            <a :href="project.repo" target="_blank" class="ui-projects__card-box__repo">
              <i class="fab fa-github" />Go to github repo
            </a>
          </div>
        </div>
      </div>
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
  .ui-projects {
    padding: 40px;
    min-height: calc(100vh - 555px);
    background-color: var(--light-primary-color);
    color: var(--dark-text-primary-color);
    user-select: none;
    @include upToTablet {
      padding: 40px 30px;
    }
    @include upToMobile {
      padding: 40px 20px;
      min-height: calc(100vh - 405px);
    }
    &__cards {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-gap: 20px;
      @include upToSmallDesktop {
        grid-template-columns: repeat(3, 1fr);
      }
      @include upToTablet {
        grid-template-columns: repeat(2, 1fr);
      }
      @include upToMobile {
        grid-gap: 10px;
      }
      @include smallMobile {
        grid-template-columns: repeat(1, 1fr);
      }
    }
    &__card {
      position: relative;
      border-radius: var(--radius);
      overflow: hidden;
      &:hover {
        .ui-projects__card-box {
          transform: translateY(0);
        }
      }
      img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center;
      }
      &-box {
        transform: translateY(100%);
        position: absolute;
        z-index: 1;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-color: rgba(var(--dark-primary-color-rgb-fixed), 0.5);
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: auto 1fr auto;
        transition: transform var(--transition) linear;
        @include upToSmallDesktop {
          transform: translateY(0);
        }
        &__name {
          background-color: var(--dark-primary-color--fixed);
          color: var(--active-color-primary);
          font-weight: 500;
          padding: 10px;
          text-align: center;
          font-size: 12px;
          text-transform: uppercase;
          transition: var(--transition) linear;
        }
        &__tech {
          padding: 10px;
          display: grid;
          grid-template-columns: repeat(3, 1fr);
          grid-gap: 10px;
          grid-template-rows: max-content;
          img {
            height: auto;
            border-radius: var(--radius);
          }
        }
        &__repo {
          text-align: center;
          display: block;
          background-color: var(--dark-primary-color--fixed);
          color: var(--always-text-light-primary);
          text-decoration: none;
          text-transform: uppercase;
          padding: 10px;
          font-size: 12px;
          transition: var(--transition) linear;
          &:hover {
            transition: none;
            color: var(--active-color-primary);
          }
          i {
            margin-right: 5px;
          }
        }
      }
    }
  }
</style>
