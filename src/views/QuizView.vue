<script setup>
import { ref, computed } from "vue";
import { useRoute } from "vue-router";

import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import quizzes from "../data/quizdata.json";
import Result from "../components/Result.vue";

const route = useRoute();
const quizId = parseInt(route.params.id);
const quiz = quizzes.find((q) => q.id === quizId);
const currentQuestionIndex = ref(0);
const correctAnswers = ref(0);
const showResults = ref(false);

const questionStatus = computed(
  () => `${currentQuestionIndex.value} / ${quiz.questions.length}`
);

const barPercent = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
);

const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    correctAnswers.value++;
  }
  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResults.value = true;
  }
  currentQuestionIndex.value++;
};
</script>

<template>
  <div>
    <QuizHeader :questionStatus="questionStatus" :barPercent="barPercent" />
    <div>
      <Question
        v-if="!showResults"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
      <Result
        v-else
        :quizQuestionLength="quiz.questions.length"
        :numberCorrect="correctAnswers"
      />
    </div>
  </div>
</template>
