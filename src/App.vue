<script setup lang="ts">
import { computed, ref } from "vue";
import Answers from "./components/Answers.vue";
import Scores from "./components/Scores.vue";
import { game } from "./game.fixture";

const currentQuestionIndex = ref(0);
const currentGameProgress = computed(() => game[currentQuestionIndex.value]);
const answersToDisplay = computed(() =>
  currentGameProgress.value.answers.map((a) => ({ content: "", points: 0 }))
);
const possibleAnswers = computed(() => currentGameProgress.value.answers);
</script>

<template>
  <main>
    <section>
      <card class="question"> {{ currentGameProgress.question }} ? </card>
    </section>
    <section class="wrapper">
      <Answers :answers="answersToDisplay" />
    </section>
    <Scores />
  </main>
</template>

<style scoped>
.question {
  font-size: 50px;
  padding: 5px;
}
main {
  display: flex;
  flex-direction: column;
}
.wrapper {
  display: flex;
  justify-content: space-between;
  min-width: 70vw;
}
</style>
