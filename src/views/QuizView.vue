<script setup>
import { useRoute } from "vue-router";
import { ref, computed } from "vue";
import quizzes from "../data/quizzes.json";
import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import Result from "../components/Result.vue";

const route = useRoute();
const quizID = parseInt(route.params.id);
const quiz = quizzes.find((q) => q.id === quizID);
const quizScore = ref(0);
const currentQuestionIndex = ref(0);
const display = ref(false);

const scoreText = computed(() => `${quizScore.value}/${quiz.questions.length}`);

const questionStatus = computed(
  () => `${currentQuestionIndex.value}/${quiz.questions.length}`
);

const barPercentage = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
);

const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    quizScore.value++;
  }
  currentQuestionIndex.value++;

  if (currentQuestionIndex.value === quiz.questions.length) {
    display.value = true;
    return;
  }
};
</script>

<template>
  <div>
    <QuizHeader :status="questionStatus" :barPercentage="barPercentage" />
    <div v-if="!display">
      <Question
        :questions="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
    </div>
    <div v-else>
      <Result :result="scoreText" />
    </div>
  </div>
</template>
