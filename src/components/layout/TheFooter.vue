<template>
  <footer :class="$style.footer">
    <div :class="[$style['footer__icons'], 'container']">
      <SocialIcons/>
    </div>
  </footer>
</template>

<script>
import SocialIcons from "@/components/footer/SocialIcons";

export default {
  name: "TheFooter",
  components: {
    SocialIcons,
  }
}
</script>

<style lang="scss" module>
.footer {
  background: $blue-dark;
  min-height: 30rem;
  @media (max-width: $level_7) {
    min-height: auto;
  }

  &__icons {
    display: flex;
    justify-content: flex-end;
    @media (max-width: $level_7) {
      justify-content: flex-start;
    }
  }
}
</style>
