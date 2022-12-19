<script setup lang="ts">
const answers = [
  {
    content: "Australia",
    points: 26,
  },
  {
    content: "Afghanistan",
    points: 21,
  },
  {
    content: "America",
    points: 18,
  },
  {
    content: "Albania",
    points: 13,
  },
  {
    content: "Algeria",
    points: 6,
  },
  {
    content: "Argentina",
    points: 4,
  },
  {
    content: "Armenia",
    points: 2,
  },
];
</script>
<template>
  <card
    class="card flex"
    v-for="(answer, position) in answers"
    :key="answer.content"
  >
    <div class="position">{{ position + 1 }}</div>
    <div class="content">{{ answer.content }}</div>
    <div class="points">{{ answer.points }}</div>
  </card>
</template>

<style scoped>
* {
  font-size: 60px;
}
.flex {
  display: flex;
  justify-content: space-between;
}

.flex > div {
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
  flex-basis: 12%;
  max-width: 12%;
  background-color: pink;
}
</style>
