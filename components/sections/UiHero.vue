<template>
  <div class="ui-hero">
    <client-only>
      <ui-particles
        class="ui-hero__particles"
        color="#27293d"
        :particles-number="100"
        shape-type="polygon"
        :particle-size="5"
        movement-direction="top"
        lines-color="#CC0000"
        :line-linked="false"
        :move-speed="0.75"
      />
    </client-only>
    <div class="ui-hero__me">
      <div class="ui-hero__line" />
      <h1>I'm <strong>Nemanja Dragun</strong></h1>
      <h6>Full-stack <strong>Web Developer</strong></h6>
    </div>
    <div class="g-container ui-hero__bottom-bar">
      <div>
        <a href="https://facebook.com">
          <i class="fab fa-facebook-f" />
        </a>
        <a href="https://facebook.com">
          <i class="fab fa-twitter" />
        </a>
        <a href="https://facebook.com">
          <i class="fab fa-linkedin-in" />
        </a>
        <a href="https://facebook.com">
          <i class="fab fa-discord" />
        </a>
        <a href="https://facebook.com">
          <i class="fab fa-skype" />
        </a>
      </div>
      <div>
        <span><i class="fas fa-mouse" /></span>
        <div>
          Scroll down
        </div>
      </div>
      <div>
        <span><i class="fab fa-github" /> <a href="https://github.com/ndragun92" target="_blank">github.com/ndragun92</a></span>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .ui-hero {
    position: relative;
    background-color: var(--always-dark-primary);
    color: var(--always-text-light-primary);
    height: 100vh;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    /*clip-path: polygon(100% 0%, 98% 90%, 50% 98%, 50% 98%, 2% 90%, 0 0);*/
    clip-path: polygon(100% 0%, 100% 90%, 50% 98%, 50% 98%, 0 90%, 0 0);
    &:before {
      content: '';
      background-image: url("~static/images/sections/hero3.svg");
      background-repeat: no-repeat;
      background-size: auto;
      background-position: bottom center;
      opacity: 0.1;
      position: absolute;
      z-index: $z_index-absolute;
      top: 0;
      right: 0;
      bottom: 20px;
      left: 0;
    }
    &__particles {
      position: absolute;
      z-index: $z_index-absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      pointer-events: none;
    }
    &__line {
      margin: 0 auto 10px auto;
      width: 100px;
      border-bottom: 3px solid var(--active-color-primary);
    }
    &__me {
      display: flex;
      flex-direction: column;
      pointer-events: none;
      h1 {
        text-transform: uppercase;
        letter-spacing: 1px;
        margin: 0 0 5px 0;
        font-size: 40px;
        font-weight: 400;
        strong {
          color: var(--active-color-primary);
        }
      }
      h6 {
        display: inline-block;
        letter-spacing: 1px;
        text-transform: uppercase;
        margin: 0 0 0 auto;
        font-size: 14px;
        font-weight: 400;
      }
    }
    &__bottom-bar {
      position: absolute;
      z-index: $z_index-absolute;
      right: 0;
      bottom: calc(10% + 40px);
      left: 0;
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-gap: 10px;
      align-items: center;
      & > div {
        &:nth-child(1) {
          display: flex;
          align-items: center;
          a {
            $size: 45px;
            background-color: transparent;
            border: 2px solid var(--always-text-light-primary);
            color: var(--always-text-light-primary);
            font-size: 16px;
            text-decoration: none;
            display: flex;
            align-items: center;
            justify-content: center;
            width: $size;
            height: $size;
            border-radius: 100%;
            margin: 0 10px;
            transition: 0.2s linear;
            &:first-child {
              margin-left: 0;
            }
            &:last-child {
              margin-right: 0;
            }
            &:hover {
              transition: none;
              border-color: var(--active-color-primary);
              background-color: var(--active-color-primary);
              color: var(--dark-text-primary-color)
            }
          }
        }
        &:nth-child(2) {
          justify-self: center;
          text-align: center;
          i {
            font-size: 18px;
          }
          & > div {
            margin-top: 10px;
            font-size: 9px;
            text-transform: uppercase;
          }
        }
        &:nth-child(3) {
          justify-self: flex-end;
          i {
            vertical-align: middle;
            font-size: 20px;
            margin-right: 5px;
          }
          a {
            text-decoration: none;
            color: var(--active-color-primary);
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
  }
</style>
<script>
import UiParticles from '../UiParticles'
export default {
  components: { UiParticles }
}
</script>
