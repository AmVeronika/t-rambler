<template>
  <section :class="$style['history-voting']">
    <div class="container"
             :class="$style['history-voting__wrapp']">
      <div :class="$style['history-voting__block']">
        <p :class="$style['history-voting__text']">
          С 17 по 19 сентября пройдут всероссийские выборы в Госдуму. Кроме того, жители нескольких районов столицы
          будут
          голосовать за депутатов Мосгордумы и муниципальных советов. На всех выборах москвичи смогут проголосовать
          онлайн. Эта опция доступна жителям столицы старше 18 лет с полной учетной записью на mos.ru. Регистрация для
          участия в электронном голосовании уже началась и будет продолжаться до 23:59 13 сентября, само голосование
          пройдет с 08:00 17 сентября до 20:00 19 сентября.
          Рассказываем, с какими технологиями встретятся избиратели на этих выборах.
        </p>
        <SpaceBlock :class="$style['space-block']">
          Безопасность электронного голосования и анонимность избирателей обеспечиваются сразу несколькими
          технологиями.
          Среди
          них блокчейн, шифрование и анонимайзер.
        </SpaceBlock>
<!--      </div>-->
<!--      <div :class="$style['history-voting__block']">-->
        <VButton size="medium"
                 :class="$style['button']">
          Записаться на онлайн-голосование
        </VButton>
      </div>
    </div>
  </section>
</template>

<script>
import SpaceBlock from "@/components/ui/SpaceBlock"
import VButton from "@/components/ui/button/VButton";

export default {
  name: "HistoryVoting",
  components: {SpaceBlock, VButton},
}
</script>

<style lang="scss" module>
.history-voting {
  padding: 5rem 0;
  background: url("../assets/image/lines-rot.png") no-repeat right 6% top 60%;
  @media (max-width: $level_2) {
    background-size: 39%;
    background-position-y: 90%;
  }
  @media (max-width: $level_4) {
    background-size: 43%;
    background-position-y: 73%;
  }
  @media (max-width: $level_6) {
    padding: 2rem 0 5rem;
  }
  @media (max-width: $level_9) {
    background: url("../assets/image/lines-rot.png") no-repeat center bottom 8% / 80%;
  }
  & .history-voting__wrapp {
    display: flex;
    justify-content: center;
    flex-direction: column;
  }

  &__block {
    display: grid;
    grid-template-columns: 65rem minmax(20rem, 50rem);
    grid-template-rows: auto auto;
    column-gap: 9rem;
    row-gap: 5rem;
    margin-left: 7rem;
    @media (max-width: $level_4) {
      grid-template-columns: minmax(32rem, 52rem) minmax(10rem, 30rem);
      column-gap: 5rem;
      margin-left: 4rem;
    }
    @media (max-width: $level_6) {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-left: 0;
      & .button {
        max-width: 90%;
        margin-top: 2rem;
      }
      &__text {
        width: 80%;

      }
    }
      & .button {
        max-width: 47.5rem;
        width: 100%;
      }
  }

  &__text {
    max-width: 65rem;
    width: 100%;
    font-weight: 500;
    font-size: 2.6rem;
    line-height: 153.4%;
    color: $blue-dark;
  }

}

</style>
