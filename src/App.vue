<script setup lang="ts">
import { computed, ref, type Ref } from "vue";
import Answers from "./components/Answers.vue";
import Scores from "./components/Scores.vue";
import { game } from "./game.fixture";

const currentQuestionIndex = ref(0);
const currentGameProgress = computed(() => game[currentQuestionIndex.value]);
const answersToDisplay = computed(() =>
  currentGameProgress.value.answers.map((a, i) =>
    [...correctAnswers.value].includes(i) ? a : { content: "", points: 0 }
  )
);

const currentFamily = ref("A");
const families = ref({
  A: { score: 0, livesLostInRound: [] },
  B: { score: 0, livesLostInRound: [] },
});

function setCurrentFamily(family: string) {
  currentFamily.value = family;
}

function addLostLifeToCurrentFamily() {
  const c = families.value[currentFamily.value as keyof typeof families.value];
  if (c.livesLostInRound.length < 3) {
    c.livesLostInRound.push("❌");
  }
}

const correctAnswers = ref([]) as Ref<number[]>;
function setCorrectAnswer(answerIndex: number) {
  correctAnswers.value.push(answerIndex);
}
const possibleAnswers = computed(() => currentGameProgress.value.answers);
</script>

<template>
  <main class="flex-column">
    <section>
      <card class="question"> {{ currentGameProgress.question }} ? </card>
    </section>
    <section class="answers-wrapper">
      <Answers
        :answers="answersToDisplay"
        @correct-answer-submitted="setCorrectAnswer"
      >
        <template #families>
          <section class="flex-column">
            <card
              v-for="[family, data] of Object.entries(families)"
              :key="family"
            >
              <span
                @click="setCurrentFamily(family)"
                :class="currentFamily === family ? `current-family` : ``"
              >
                {{ family }}: {{ data["score"] }}
              </span>
            </card>
          </section>
        </template>
        <template #chances>
          <section class="flex-column">
            <card
              v-for="[family, data] of Object.entries(families)"
              :key="family"
            >
              <span
                v-for="(lifeLost, index) in data.livesLostInRound"
                :key="index"
                >{{ lifeLost }}</span
              >
              <button @click="addLostLifeToCurrentFamily">+</button>
            </card>
          </section>
        </template>
      </Answers>
    </section>
    <Scores />
  </main>
</template>

<style scoped>
.current-family {
  color: red;
}
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
