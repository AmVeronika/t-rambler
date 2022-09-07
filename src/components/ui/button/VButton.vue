<template>
  <div :class="$style['v-button']">
    <button :disabled="disabled"
            :class="[$style['v-button__wrapp'], ...classList]"
            @click="$emit('click', $event)"
    >
      <slot></slot>
    </button>
    <p ref="shadow" :class="$style['border']"></p>
  </div>

</template>

<script>
import {gsap} from 'gsap';
import {ScrollTrigger} from 'gsap/dist/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "VButton",

  props: {
    size: {
      type: String,
      default: 'medium',
      validator: v => [
        'medium',
      ].includes(v),
    },

    color: {
      type: String,
      default: 'orange',
      validator: v => [
        'orange',
      ].includes(v),
    },

    disabled: {
      type: Boolean,
      default: false,
    },

    active: {
      type: Boolean,
      default: false,
    },

  },

  mounted() {
    this.scroll()
  },

  computed: {
    classList() {
      return [
        this.$style[`_${this.size}`],
        this.$style[`_${this.color}`],
        {
          [this.$style._disabled]: this.disabled,
          [this.$style._hover]: this.active,
        },
      ];
    }
  },

  methods: {
    scroll() {
      gsap.to(this.$refs.shadow, {
        scrollTrigger: {
          trigger: this.$refs.shadow,
          start: "top 80%",
          // end: "bottom 20%",
          toggleActions: 'play none reverse none',
        },
        x: '7px',
        y: '9px',
        duration: .5,
      });
    }
  }
}
</script>

<style lang="scss" module>
.v-button {
  position: relative;
  width: 100%;

  & .border {
    position: absolute;
    left: 0;
    top: 0;
    width: inherit;
    height: 6.8rem;
    background: none;
    border: 2px solid #FF715E;
    border-radius: 6.7rem;
    z-index: -1;
  }

  &__wrapp {
    display: flex;
    align-items: center;
    justify-content: center;
    text-transform: inherit;
    width: inherit;
    white-space: nowrap;
    border-radius: 6.4rem;
    color: $white;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    font-weight: 800;
    font-size: 1.8rem;
    line-height: 153.4%;
    transition: .2s ease-out;
    //Состояния
    &._disabled {
      pointer-events: none;
    }

    &._active {
      pointer-events: none;
    }

    &._medium {
      padding: 2rem 3rem;
    }

    //Цвета
    &._orange {
      border: 2px solid $orange;
      background: $orange;
      color: $white;

      &:hover {
        border: 2px solid $orange-extra;
        background: $orange-extra;
        color: $white;
        transition: .2s ease-out;
      }

      &:active {
        border: 2px solid $orange;
        background: $white;
        color: $orange;
        transition: .2s ease-out;
      }
    }


    &._disabled {
      border: 1px solid #f4f4f4;
      background-color: #f4f4f4;
      color: grey;
    }
  }
}


</style>
