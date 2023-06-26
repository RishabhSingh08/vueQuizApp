<script setup>
import { useRouter } from "vue-router";

const router = useRouter();

const goBack = () => {
  router.push("/");
};

const { questionStatus, barPercent } = defineProps([
  "questionStatus",
  "barPercent",
]);
</script>

<template>
  <header>
    <h4>Question {{ questionStatus }}</h4>
    <div class="bar">
      <div class="completion" :style="{ width: barPercent }"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
  color: white;
  font-size: 30px;
}

.bar {
  width: 100%;
  height: 20px;
  border: 1px solid #333;
  background-color: #222;
  margin-bottom: 20px;
}

.completion {
  height: 100%;
  width: 0%;
  background-color: rgb(143, 143, 143);
  transition: width 0.3s ease-in-out;
}
</style>
