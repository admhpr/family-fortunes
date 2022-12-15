<script setup lang="ts">
import Answers from "./components/Answers.vue";
import Scores from "./components/Scores.vue";
</script>

<template>
  <section class="flex">
    <header>
      <img
        alt="Vue logo"
        class="logo"
        src="./assets/logo.svg"
        width="125"
        height="125"
      />

      <div class="wrapper"></div>
    </header>

    <main>
      <Answers />
      <Scores />
    </main>
  </section>
</template>

<style scoped>
.flex {
  display: flex;
  flex-direction: column;
}
</style>
