<script setup lang="ts">
defineProps<{
  answers: {
    content: string;
    points: number;
  }[];
}>();
</script>
<template>
  <section class="flex">
    <slot />
    <div class="answers-display">
      <card
        class="card flex"
        v-for="(answer, position) in answers"
        :key="answer.content"
      >
        <div class="position">{{ position + 1 }}</div>
        <div class="content">{{ answer.content }}</div>
        <div class="points">
          <span v-show="answer.points > 0">{{ answer.points }}</span>
        </div>
      </card>
    </div>
  </section>
</template>

<style scoped>
* {
  font-size: 60px;
}
section {
  margin-top: 2rem;
}

.answers-display {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  min-width: 50vw;
}
.flex {
  display: flex;
  justify-content: space-between;
}

.position {
  flex-basis: 5%;
  max-width: 5%;
  background-color: red;
}
.content {
  flex-basis: 80%;
  max-width: 80%;
  padding: 0 23rem;
  background-color: blue;
}

.points {
  flex-basis: 10%;
  max-width: 10%;
  padding: 0 0rem;

  background-color: pink;
}
</style>
