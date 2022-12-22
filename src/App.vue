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

const familyScores = ref({
  A: 0,
  B: 0,
});
const possibleAnswers = computed(() => currentGameProgress.value.answers);
</script>

<template>
  <main class="flex-column">
    <section>
      <card class="question"> {{ currentGameProgress.question }} ? </card>
    </section>
    <section class="answers-wrapper">
      <Answers :answers="answersToDisplay">
        <section class="flex-column">
          <div
            v-for="[family, score] of Object.entries(familyScores)"
            :key="family"
          >
            {{ family }}: {{ score }}
          </div>
        </section>
      </Answers>
    </section>
    <Scores />
  </main>
</template>

<style scoped>
.question {
  font-size: 50px;
  padding: 5px;
}
.flex-column {
  display: flex;
  flex-direction: column;
}
.answers-wrapper {
  display: flex;
  justify-content: space-between;
  min-width: 70vw;
}
</style>
