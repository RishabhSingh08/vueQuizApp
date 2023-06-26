<script setup>
import { useRouter } from "vue-router";

const router = useRouter();
const { quiz } = defineProps(["quiz"]);

const navigateToQuiz = () => {
  router.push(`/quiz/${quiz.id}`);
};
</script>

<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="quiz.img" alt="" />
    <div class="card-text"></div>
    <h2>{{ quiz.name }}</h2>
    <p>{{ quiz.questions.length }} Questions</p>
  </div>
</template>

<style scoped>
.card {
  width: 310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
  transition: ease-in 0.1s;
  text-align: center;
  border: 1px solid #767676;
  color: rgb(143, 143, 143);
}

.card:hover {
  transition: ease-in-out 0.2s;
  box-shadow: 0 0 30px rgba(255, 255, 255, 0.686);
}

.card img {
  width: 100%;
  height: 200px;
  object-fit: cover;
}
</style>
