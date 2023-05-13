<script setup>
import { defineProps } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const { result } = defineProps(["result"]);
</script>

<template>
  <div class="result">
    <p>Your Result</p>
    <h1>{{ result }}</h1>
    <button @click="router.push('/home')">Home</button>
  </div>
</template>

<style scoped>
.result {
  text-align: center;
  padding: 100px 0;
}

p {
  font-size: 25px;
}

h1 {
  font-size: 80px;
}
</style>
