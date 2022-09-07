<template>
  <CentralBlock id="02"
                 color="blue"  :title="title" :text="text">
    <img src="../assets/image/illustration2.png" alt="Фоновая картинка">
  </CentralBlock>
</template>

<script>
import CentralBlock from "@/views/CentralBlock";
export default {
  name: "ExplanationBlock",
  components: {
    CentralBlock,
  },
  data() {
    return {
      title: 'Как устроена система электронного голосования',
      text: 'Давайте рассмотрим по шагам, как устроена в Москве процедура электронного голосования, что происходит с нашими личными данными и результатом голосования.',
    };
  },
}
</script>

