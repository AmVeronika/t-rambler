<template>
  <CentralBlock id="03"
                 color="orange"  :title="title" :text="text">
    <img src="../assets/image/moscow.png" alt="Фоновая картинка"
    style="width: 100%; margin-left: -4rem">
  </CentralBlock>
</template>

<script>
import CentralBlock from "@/views/CentralBlock";
export default {
  name: "MoscowBlock",
  components: {
    CentralBlock,
  },
  data() {
    return {
      title: 'Москва голосует онлайн',
      text: 'Электронное голосование проводится уже в четвертый раз. Впервые оно было организовано в 2019 году на выборах в Московскую городскую Думу. Безопасность и прозрачность также основывалась на технологии блокчейн, а тайна и анонимность голосования обеспечивались при помощи специальных алгоритмов и шифрования.',
    };
  },
}
</script>
