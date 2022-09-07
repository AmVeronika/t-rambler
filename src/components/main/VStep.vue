<template>
  <div :class="$style['step']">
    <SpaceCircle :number="content.id"/>
    <div :class="$style['step__wrap']">
      <div :class="$style['step__title']">
        <h3> {{ content.title }}</h3>
        <component v-bind:is="content.icon"></component>
      </div>
      <div>
        <p> {{ content.text }} </p>
        <VButton v-if="content.button" size="medium"
                 :class="$style.button">
          {{ content.button }}
        </VButton>
      </div>
    </div>
  </div>
</template>

<script>
import SpaceCircle from "@/components/ui/SpaceCircle"
import IconRegistration from "@/components/icons/IconRegistration";
import IconCalendar from "@/components/icons/IconCalendar";
import IconQuestion from "@/components/icons/IconQuestion";
import VButton from "@/components/ui/button/VButton";

export default {
  name: "VStep",

  components: {
    SpaceCircle,
    IconRegistration,
    IconCalendar,
    IconQuestion,
    VButton,
  },

  props: {
    content: {
      type: Object,
      default: () => ({}),
    }
  }
}
</script>

<style lang="scss" module>
.step {
  &__wrap {
    display: flex;
    justify-content: center;
    gap: 14rem;
    margin-top: 1rem;
    @media (max-width: $level_4) {
      margin-top: 2rem;
    }
    @media (max-width: $level_6) {
      flex-direction: column;
      align-items: center;
      gap: 4rem;
    }

    p {
      font-weight: 500;
      font-size: 1.8rem;
      line-height: 160.9%;
      max-width: 51rem;
      width: 100%;
      color: $blue-dark;
      @media (max-width: $level_6) {
        max-width: 80rem;
      }
    }
  }

  &__title {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 30rem;
    width: 100%;
    @media (max-width: $level_6) {
      max-width: 50rem;
    }
    h3 {
      font-weight: 700;
      font-size: 3rem;
      line-height: 122.4%;
      color: $blue-dark;
      margin-bottom: 3rem;
    }
  }

  & .button {
    margin-top: 3.5rem;
    text-transform: uppercase;
    max-width: 23rem;
    width: 100%;
    @media (max-width: $level_6) {
      max-width: 40rem;
      margin-left: auto;
      margin-right: auto;
    }
  }
}
</style>
