<script setup>
import { defineProps, defineEmits } from "vue";

const emit = defineEmits(["selectOption"]);
const { questions } = defineProps(["questions"]);

const emitSelectOption = (isCorrect) => {
  emit("selectOption", isCorrect);
};
</script>

<template>
  <div>
    <div class="question-container">
      <h1 class="question">{{ questions.text }}</h1>
    </div>
    <div class="options-container">
      <div
        v-for="option in questions.options"
        :key="option.id"
        class="option"
        @click="emitSelectOption(option.isCorrect)"
      >
        <p class="option-label">{{ option.label }}</p>
        <div class="option-value">
          <p>{{ option.text }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.question-container {
  margin-top: 20px;
}

.question {
  font-size: 40px;
  margin-bottom: 20px;
}

.option {
  display: flex;
  margin-bottom: -40px;
  cursor: pointer;
}

.option-label {
  background-color: bisque;
  width: 40px;
  height: 40px;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.option-value {
  background-color: rgb(244, 239, 239);
  width: 100%;
  height: 40px;
  margin-top: 30px;
  font-size: 30px;
  padding: 0 30px;
}

.option-value p {
  margin-top: 0;
  padding-top: 5px;
  font-size: 25px;
}

.options-container {
  margin-bottom: 30px;
}
</style>
