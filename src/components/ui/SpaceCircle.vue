<template>
  <div :class="$style['v-space']">
    <div :class="$style['v-space-block']">
      <div :class="$style['v-space-block__wrapp']">
        {{ number }}
      </div>
      <p :class="$style['border']"></p>
    </div>
    <svg :class="$style.line" viewBox="0 0 1172 104" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M1162 97.7035L1162 41.7036C1162 19.6122 1144.09 1.70362 1122 1.70362L-8.39258e-06 1.70372"
            stroke="#376EFF" stroke-width="2"/>
      <circle cx="1161.75" cy="94.0796" r="9.75343" fill="#376EFF"/>
    </svg>
  </div>
</template>

<script>

export default {
  name: "SpaceCircle",
  props: {
    number: {
      type: String,
      default: '',
    }
  },
  data() {
    return {
      windowTel: null,
    }
  },
  mounted() {
   this.windowTel = window.innerWidth;
  },
  methods: {

  }
}
</script>

<style lang="scss" module>
.v-space {
  display: flex;
  width: inherit;
  justify-content: flex-start;
  align-items: center;
  position: relative;

  &-block {
    position: relative;
    width: 8rem;
    height: 8rem;
    z-index: 2;
    &__wrapp {
      width: 8rem;
      height: 8rem;
      display: flex;
      justify-content: center;
      align-items: center;
      font-weight: 400;
      font-size: 3rem;
      line-height: 153.4%;
      color: $blue;
      background: $white;
      border: 2px solid $blue;
      border-radius: 50%;
    }

    & .border {
      position: absolute;
      right: 0;
      bottom: 0;
      transform: translate(1rem, 1rem);
      width: inherit;
      height: 100%;
      background: $blue;
      border: 2px solid $blue;
      border-radius: 50%;
      z-index: -1;
    }
  }
}

.line {
  max-width: 117rem;
  width: 100%;
  height: 10rem;
  position: absolute;
  top: 50%;
  left: 59px;
  @media (max-width: $level_1) {
    max-width: 110rem;
  }
  @media (max-width: $level_3) {
    max-width: 100rem;
  }
  @media (max-width: $level_5) {
    max-width: 95rem;
  }
  @media (max-width: $level_6) {
    max-width: 80rem;
    left: 40px;
    top: 48%;
  }
  @media (max-width: $level_7) {
    max-width: 70rem;
    left: 40px;
    top: 48%;
  }
  @media (max-width: $level_8) {
    max-width: 60rem;
    left: 40px;
    top: 48%;
  }
}

</style>
