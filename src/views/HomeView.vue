<script setup>
import quiz from "../data/quizzes.json";
import { ref, watch } from "vue";
import Card from "../components/Card.vue";

const quizzes = ref(quiz);
const search = ref("");

watch(search, () => {
  quizzes.value = quiz.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <div class="container">
    <header>
      <h1>Quizzes</h1>
      <input v-model.trim="search" type="text" placeholder="Search..." />
    </header>
    <div class="options-container">
      <Card v-for="(quiz, index) in quizzes" :key="index" :quiz="quiz" />
    </div>
  </div>
</template>

<style scoped>
header {
  margin-bottom: 10px;
  margin-top: 10px;
  display: flex;
  align-items: center;
}

h1 {
  margin-right: 30px;
  font-weight: bold;
}

header input {
  border: none;
  padding: 10px;
  border-radius: 5px;
  background-color: rgba(128, 128, 128, 0.1);
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}
</style>
