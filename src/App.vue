<template>
  <TheHeader/>
  <HistoryVoting/>
  <ExplanationBlock/>
  <StepsBlock/>
  <MoscowBlock/>
  <TheFooter/>
</template>

<script>

import TheHeader from "@/components/layout/TheHeader";
import HistoryVoting from "@/views/HistoryVoting";
import ExplanationBlock from "@/views/ExplanationBlock";
import StepsBlock from "@/views/StepsBlock";
import MoscowBlock from "@/views/MoscowBlock";
import TheFooter from "@/components/layout/TheFooter";

export default {
  name: 'App',
  components: {
    TheHeader,
    HistoryVoting,
    ExplanationBlock,
    StepsBlock,
    MoscowBlock,
    TheFooter,
  },
}

</script>

<style>
</style>
