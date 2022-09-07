<template>
  <div>
    <div :class="$style['v-space-block']">
      <div :class="$style['v-space-block__wrapp']">
        <slot></slot>
      </div>
      <p ref="shadow" :class="$style['border']"></p>
    </div>
  </div>
</template>

<script>
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/dist/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "SpaceBlock",
  mounted() {
    this.scroll()
  },
  methods: {
    scroll() {
      gsap.to(this.$refs.shadow, {
        scrollTrigger: {
          trigger: this.$refs.shadow,
          start: "top 60%",
          end: "bottom 60%",
          toggleActions: 'play none reverse none',
        },
        x: '2.8rem',
        y: '2.8rem',
        duration: .5,
      });
    }
  }
}
</script>

<style lang="scss" module>
.v-space-block {
  position: relative;
  width: 32rem;

  &__wrapp {
    font-weight: 600;
    font-size: 1.8rem;
    line-height: 153.4%;
    color: $blue;
    padding: 4.2rem 2.7rem;
    background: $white;
    border: 2px solid $blue;
    border-radius: 4rem;
  }

  & .border {
    position: absolute;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;
    background: $blue;
    border: 2px solid $blue;
    border-radius: 4rem;
    z-index: -1;
  }
}
</style>
