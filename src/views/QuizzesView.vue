<script setup>
import Card from "../components/card.vue";
import q from "../data/quizdata.json";
import { ref, watch } from "vue";

const quizzes = ref(q);
const search = ref("");

watch(search, () => {
  quizzes.value = q.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <div>
    <nav class="navbar">
      <div class="navbar-container">
        <h1 class="navbar-logo">Coding Quizzes</h1>
        <input
          class="search"
          v-model.trim="search"
          type="text"
          placeholder="Search..."
        />
      </div>
    </nav>
    <div class="options-container">
      <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>

<style scoped>
nav.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #181818;
  padding: 10px;
  z-index: 999;
  border-bottom: 2px solid #767676;
}

.navbar-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: 1200px;
  margin: 0 auto;
}

.navbar-logo {
  font-weight: bold;
  color: white;
  font-size: 40px;
}

.search {
  border: none;
  background-color: transparent;
  border-bottom: 2px solid #767676;
  padding: 10px;
  border-radius: 0;
  width: 35%;
  color: white;
  font-size: 16px;
  transition: 0.3s ease-in-out;
}

.search:focus {
  outline: none;
  border-color: white;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
  padding-top: 60px;
}
</style>
