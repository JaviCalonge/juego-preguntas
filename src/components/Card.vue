<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter()
const {quiz} = defineProps(["quiz"])

const navigateToQuiz = () => {
  router.push(`/quiz/${quiz.id}`)
}

</script>

<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="quiz.img" alt="" />
    <div class="card-text">
      <h2>{{ quiz.name }}</h2>
      <p>{{ quiz.questions.length }} Preguntas</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  background-color: white;
  width: 350px;
  height: 250px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 12px 12px 12px rgba(0, 0, 0, 0.5);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  flex-direction: column;
}
.card img {
  width: 350px;
  height: 190px;
  margin: 0 auto;
}
.card-text {
  padding: 0 15px;
  margin-bottom: 4px;
}
.card-text h2 {
  font-weight: bold;
}

@media (max-width: 1110px) {
  .card {
    width: 300px;
    height: 250px;
  }
}
</style>