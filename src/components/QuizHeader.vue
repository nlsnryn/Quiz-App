<script setup>
import { defineProps } from "vue";

const { status, barPercentage } = defineProps(["status", "barPercentage"]);
</script>

<template>
  <header>
    <h1>Question {{ status }}</h1>
    <div class="bar">
      <div class="completion" :style="{ width: barPercentage }"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  margin-top: 30px;
}

header h1 {
  font-size: 30px;
}

.bar {
  width: 300px;
  height: 25px;
  border: 3px solid bisque;
}

.completion {
  height: 100%;
  width: 0;
  background-color: bisque;
}
</style>
