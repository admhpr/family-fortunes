<script setup lang="ts">
defineProps<{
  answers: {
    content: string;
    points: number;
  }[];
}>();
</script>
<template>
  <section>
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
  </section>
</template>

<style scoped>
* {
  font-size: 60px;
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
  flex-basis: 30%;
  max-width: 30%;
  padding: 0 3rem;

  background-color: pink;
}
</style>
