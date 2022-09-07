<template>
  <div :class="$style.navigation">
    <IconArrowRight :class="$style['navigation__arrow']"/>
    <div :class="$style['navigation__sections']">
      <NavButton position="row" @checkSection="openMenu($event.evt, $event.sections, 'row')"/>
      <p :class="$style['navigation__text']">Разделы</p>
    </div>
    <BurgerMenu @showMenu="openMenu($event, false)" :open="open"/>
  </div>
</template>

<script>
import IconArrowRight from "@/components/icons/IconArrowRight";
import BurgerMenu from "@/components/icons/BurgerMenu";
import NavButton from "@/components/NavButton";

export default {
  name: "VNavigation",
  components: {
    IconArrowRight,
    BurgerMenu,
    NavButton,
  },
  props: {
    open: {
      type: Boolean,
      default: false,
    }
  },

  methods: {
    openMenu(evt, sections, position) {
      this.$emit("showMenu", {evt, sections, position});
    },
  },
}
</script>

<style lang="scss" module>
.navigation {
  display: flex;
  justify-content: space-between;
  align-items: baseline;

  &__sections {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 18.8rem;
    position: relative;
  }

  &__arrow {
    color: $white;
    margin-right: 2.4rem;
  }

  &__text {
    position: absolute;
    bottom: -1.5rem;
    left: -3rem;
    color: $white;
    font-weight: 600;
    font-size: 1.2rem;
  }
  @media (max-width: $level_6) {
    &__sectios, &__arrow, &__text {
      display: none;
    }
  }
}
</style>
