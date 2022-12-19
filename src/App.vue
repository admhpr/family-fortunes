<script setup lang="ts">
import Answers from "./components/Answers.vue";
import Scores from "./components/Scores.vue";
// import { game } from "./game.fixture";

const question = "What is the most populous country in the world?";
</script>

<template>
  <section class="wrapper">
    <header>
      <card class="question">
        {{ question }}
      </card>
    </header>

    <main>
      <Answers />
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
}
</style>
