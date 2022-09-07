<template>
  <header id="01"
          :class="$style.header">
    <nav :class="$style['header__wrapp']">
      <a href="#">
        <IconLogo :class="$style['header__logo']"/>
      </a>
      <VNavigation @showMenu="openMenu($event)" :open="open"/>
    </nav>
    <div :class="$style.container">
      <h1>Все об онлайн-голосовании в Москве</h1>
    </div>
    <MenuBlock v-if="open" @hideModal="open">
      <NavButton position="col" @checkSection="openMenu({$event})"/>
    </MenuBlock>
  </header>
</template>

<script>
import IconLogo from "@/components/icons/IconLogo";
import VNavigation from "@/components/header/VNavigation";
import MenuBlock from "@/components/MenuBlock";
import NavButton from "@/components/NavButton";

export default {
  name: "TheHeader",
  components: {
    IconLogo,
    VNavigation,
    MenuBlock, NavButton,
  },
  data() {
    return {
      open: false,
      sections: [],
    };
  },
  methods: {
    openMenu(evt) {
     evt.position !== 'row' ? this.open = evt.evt : false;
      this.sections = evt.sections;
    },
  },
}
</script>

<style lang="scss" module>
.header {
  min-height: 100vh;
  background: url("../../assets/image/lines.png") no-repeat left 2% bottom 12% / auto,
  url("../../assets/image/IllustrationPC.png") no-repeat right bottom 8% / auto,
  url("../../assets/image/Illustration.png") no-repeat right top / auto,
  $blue;
  @media (max-width: $level_1) {
    background: url("../../assets/image/lines.png") no-repeat left 2% bottom 22% / 30%,
    url("../../assets/image/IllustrationPC.png") no-repeat right bottom 15% / 70%,
    url("../../assets/image/Illustration.png") no-repeat right top / 43%,
    $blue;
  }
  @media (max-width: $level_4) {
    background: url("../../assets/image/lines.png") no-repeat left 2% bottom 25% / 30%,
    url("../../assets/image/IllustrationPC.png") no-repeat right bottom 25% / 70%,
    url("../../assets/image/Illustration.png") no-repeat right top / 43%,
    $blue;
  }
  @media (max-width: $level_7) {
    background: url("../../assets/image/IllustrationPC.png") no-repeat right bottom / 100%,
    url("../../assets/image/Illustration.png") no-repeat right center / 60%,
    $blue;
  }
  @media (max-width: $level_9) {
    background: url("../../assets/image/IllustrationPC.png") no-repeat bottom 30% center / 100%,
    url("../../assets/image/Illustration.png") no-repeat bottom  center / 100%,
    $blue;
  }

  & h1 {
    max-width: 67.5rem;
    width: 100%;
    font-weight: 700;
    font-size: 7rem;
    line-height: 8.2rem;
    text-transform: uppercase;
    color: $white;
    margin-top: 12rem;
    @media (max-width: $level_9) {
      margin-top: 25%;
    }
  }

  & > .container {
    min-height: 100vh;
    max-width: 134rem;
    margin: 0 auto;
    padding: 3rem;
    width: 100%;
    @media (max-width: $level_7) {
      padding: 3rem 8rem;
    }
    @media (max-width: $level_9) {
      margit-top: 4rem;
    }
  }

  &__wrapp {
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    justify-content: space-between;
    padding: 3rem 5rem 2rem;
    margin: 0 auto;
    width: 100%;
    background: $blue;
    z-index: 100;
    @media (max-width: $level_7) {
      padding: 9rem 5rem 2rem;
    }
  }

  &__logo {
    color: $white;
  }
}
</style>
