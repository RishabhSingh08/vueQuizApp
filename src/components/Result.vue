<script setup>
import { useRouter } from "vue-router";

const { quizQuestionLength, numberCorrect } = defineProps([
  "quizQuestionLength",
  "numberCorrect",
]);

const router = useRouter();

const goBack = () => {
  router.push("/");
};
</script>

<template>
  <div class="results">
    <p>Your Results...</p>
    <h1>{{ numberCorrect }} / {{ quizQuestionLength }}</h1>
    <button @click="goBack">Go Back</button>
  </div>
</template>

<style scoped>
.results {
  text-align: center;
  padding: 100px 0px;
  color: #fff; /* Set text color to white */
}

p {
  font-size: 25px;
}

h1 {
  font-size: 80px;
  color: #fff; /* Set heading color to white */
}

button {
  cursor: pointer;
  font-size: 16px;
  border-radius: 8px;
  padding: 10px 20px;
  border: 1px solid #a9a9a9;
  background: #fff;
  color: #222222;
  text-decoration: none;
  color: rgb(255, 255, 255);
  background-color: #333; /* Dark background color for button */
}
</style>
