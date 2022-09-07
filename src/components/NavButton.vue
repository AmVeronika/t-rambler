<template>
  <div :class="[$style['navigation__block'],
              {[$style['block-col']] : position === 'col'},
              {[$style['hidden']] : position === 'row'} ]">
    <button v-for="section in sections"
            :key="section.id"
            @click="scrollTo(section.id)"
            :class="[$style['navigation__section'], { [$style['active']]: activeSection === section.id }]"> {{ section.id }}
      <span v-if="position === 'col'" :class="[{[$style['block-col-name']] : position === 'col'}]">{{ section.name }} </span>
    </button>
    <p :class="[$style['navigation__line'], {[$style['line-col']] : position === 'col'}]"></p>
  </div>
</template>

<script>
export default {
  name: 'NavButton',
  props:
      {
        position: {
          type: String,
          default: 'row'
        },
      },
  data() {
    return {
      sections: [{id: '01', name: 'в начало'},
        {id: '02', name: 'Как устроена система электронного голосования'},
        {id: '03', name: 'Москва голосует онлайн'}],
      activeSection: '01',
    };
  },
  methods: {
    scrollTo(id, offset = 100) {
      this.activeSection = id;
      const target = document.getElementById(id);
      if (target) {
        const position =
            target.getBoundingClientRect().top + window.pageYOffset;
        window.scroll({
          top: position - offset,
          left: 0,
          behavior: 'smooth',
        });
      }
      this.$emit("checkSection", {evt: false, sections: id});
    },
  },
};
</script>

<style lang="scss" module>
.navigation {
  &__block {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    position: relative;
  }

  &__section {
    display: flex;
    align-items: center;
    justify-content: center;
    min-width: 2.8rem;
    min-height: 2.8rem;
    max-width: 2.8rem;
    max-height: 2.8rem;
    font-weight: 400;
    font-size: 1.4rem;
    color: $white;
    background: $blue;
    border: .1rem solid $white;
    border-radius: 100%;
    position: relative;
    z-index: 2;

    &:hover {
      background: $white;
      color: $blue;
    }
  }

  &__line {
    position: absolute;
    display: flex;
    width: 100%;
    height: .1rem;
    background: $white;
    z-index: 1;
  }
}
.block-col {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height: 250px;
  position: relative;
  margin-left: 14rem;
  margin-right: 100%;
  &-name {
    position: absolute;
    left: 6rem;
    width: 257px;
    text-align: left;
    font-weight: 700;
    font-size: 18px;
    line-height: 21px;
    text-transform: uppercase;
    color: $white;
  }
  & > button {
    min-width: 5.2rem;
    min-height: 5.2rem;
  }
}
.line-col {
  width: 1px;
  height: inherit;
}
.active {
  background: $white;
  color: $blue;
}
.hidden {
  @media (max-width: $level_6) {
    display: none;
  }
}
</style>
