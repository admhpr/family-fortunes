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
  <section class="wrapper">
    <header>
      <card class="question"> {{ currentGameProgress.question }} ? </card>
    </header>

    <main>
      <Answers :answers="answersToDisplay" />
      <Scores />
    </main>
  </section>
</template>

<style scoped>
.question {
  font-size: 50px;
  padding: 5px;
}
.wrapper {
  display: flex;
  flex-direction: column;
  min-width: 70vw;
}
</style>
