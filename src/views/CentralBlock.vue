<template>
  <section :class="[$style.central, classList]">
    <div class="container" :class="$style['central__container']">
      <div :class="$style['central__img']">
        <slot></slot>
      </div>
      <div :class="$style['central__wrap']">
        <h2> {{ title }}</h2>
        <p> {{ text }}</p>
      </div>
    </div>
  </section>
</template>

<script>

export default {
  name: "CentralBlock",

  props: {
    title: {
      type: String,
      default: '',
    },
    text: {
      type: String,
      default: '',
    },
    color: {
      type: String,
      default: 'blue',
      validator: v => [
        'orange', 'blue'
      ].includes(v),
    },
  },
  computed: {
    classList() {
      return this.$style[`_${this.color}`];
    }
  }

}
</script>

<style lang="scss" module>
.central {
  min-height: 100vh;
  @media (max-width: $level_3) {
    background: none;
  }
  @media (max-width: $level_7) {
    min-height: auto;
  }

  &._orange {
    background: url("../assets/image/lines2.png") no-repeat right 5% bottom 5%, $orange;

    .central__wrap {
      background: rgba(255, 113, 94, 0.68);
    }

    @media (max-width: $level_4) {
      background: $orange;
    }
  }

  &._blue {
    background: url("../assets/image/lines2.png") no-repeat right 5% bottom 5%, $blue;

    .central__wrap {
      background: rgba(55, 110, 255, 0.74);
    }

    @media (max-width: $level_4) {
      background: $blue;
    }
  }

  &__container {
    display: grid;
    justify-content: center;
    align-items: start;
    grid-template-columns: minmax(34rem, 65rem) minmax(34rem, 51rem);
    min-height: inherit;
    @media (max-width: $level_6) {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    @media (max-width: $level_7) {
      min-width: 33.4rem;
      max-width: 80rem !important;
    }
  }

  &__img {
    & img {
      width: 100%;
      margin-left: -4rem;
    }
    @media (max-width: $level_6) {
      width: 80%;
      & img {
        margin-left: 0;
      }
    }
  }

  &__wrap {
    display: flex;
    flex-direction: column;
    max-width: 51rem;
    width: 100%;
    color: $white;
    margin-top: 10rem;
    @media (max-width: $level_6) {
      max-width: none;
      width: 90%;
      margin: 5rem 0;
    }
    & h2 {
      font-weight: 700;
      font-size: 4.5rem;
      line-height: 122.4%;
      margin-bottom: 4rem;
      text-transform: uppercase
    }

    & p {
      font-weight: 500;
      font-size: 2.6rem;
      line-height: 153.4%;
    }
  }
}

</style>
