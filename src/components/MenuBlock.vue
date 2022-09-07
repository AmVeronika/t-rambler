<template>
  <div class="menu" @click.self="showModal">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'MenuBlock',
  methods: {
    showModal() {
      this.$emit('hideModal', false);
    },
  },
};
</script>

<style lang='scss'>
.menu {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  bottom: 0;
  min-width: 100vw;
  min-height: 100%;
  left: 0;
  right: 0;
  z-index: 11;
  background: $blue;
}

@keyframes ani {
  0% {
    transform: translateY(-8%);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}
</style>
