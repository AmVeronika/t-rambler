<template>
  <ul :class="$style['social-icons']">
    <li><a href="#"><IconVk :class="$style['social-icons__icon']"/></a></li>
    <li><a href="#"><IconFacebook :class="$style['social-icons__icon']"/></a></li>
    <li><a href="#"><IconTwitter :class="$style['social-icons__icon']"/></a></li>
  </ul>
</template>

<script>
import IconVk from "@/components/icons/social/IconVk";
import IconFacebook from "@/components/icons/social/IconFacebook";
import IconTwitter from "@/components/icons/social/IconTwitter";

export default {
  name: "SocialIcons",
  components: {
    IconVk,
    IconFacebook,
    IconTwitter,

  },
}
</script>

<style lang="scss" module>
.social-icons {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  width: 20rem;
  @media (max-width: $level_7) {
    width: 22rem;
    margin: 4.7rem 0 8.6rem 2.5rem;
  }
  @media (max-width: $level_6) {
    width: 42rem;
  }
  &__icon {
    color: $white;
    transition: .2s ease-out;
    &:hover {
      transition: .2s ease-out;
      color: $orange;
    }
  }
}
</style>
