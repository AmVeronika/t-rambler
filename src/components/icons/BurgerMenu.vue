<template>
  <button ref="menu" class="nav-toggle" @click="showMenu">
    <span class="bar-top"></span>
    <span class="bar-mid"></span>
    <span class="bar-bot"></span>
  </button>
</template>

<script>

export default {
  name: "BurgerMenu",
  props: {
    open: {
      type: Boolean,
      default: false,
    }
  },
  data() {
    return {
      openMenu: false,
    };
  },
  watch: {
    open: {
      handler() {
        if (!this.open && this.openMenu) {
          this.showMenu()
        }
      },
      deep: true
    },
  },
  methods: {
    showMenu() {
      const menu = this.$refs.menu;
      menu.classList.toggle('opened');
      this.openMenu = !this.openMenu;
      console.log('openMenu', this.openMenu)
      this.$emit("showMenu", this.openMenu);
    }
  },
}
</script>
<style lang="scss">
.nav-toggle {
  //transform: translate(-50%, -50%);
  width: 20px;
  margin-left: 2rem;
  @media (min-width: $level_6) {
    display: none;
  }
}

.nav-toggle:focus {
  outline-width: 0;
}

.nav-toggle [class*='bar-'] {
  background: $white;
  display: block;
  transform: rotate(0deg);
  transition: .2s ease all;
  height: 1.5px;
  margin-bottom: 3px;

}

.nav-toggle .bar-bot {
  margin-bottom: 0;
}

.opened .bar-top {
  transform: rotate(45deg);
  transform-origin: 15% 15%;
}

.opened .bar-mid {
  opacity: 0;
}

.opened .bar-bot {
  transform: rotate(-45deg);
  transform-origin: 15% 95%;
}
</style>

