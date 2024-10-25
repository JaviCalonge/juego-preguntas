<script setup>
import { defineProps, onMounted } from "vue";
import { RouterLink } from "vue-router";

const { quizQuestionLength, numberOfCorrectAnswer } = defineProps([
  "quizQuestionLength",
  "numberOfCorrectAnswer",
]);

onMounted(() => {
  if (numberOfCorrectAnswer === quizQuestionLength) {
    // Disparar confeti usando canvas-confetti
    confetti({
      particleCount: 200,
      spread: 70,
      origin: { y: 0.6 }
    });
    confetti({
  particleCount: 200,
  angle: 90,
  spread: 90,
  origin: { x: 0.5, y: 1 }, // Desde el centro inferior
  colors: ['#f0f', '#0ff', '#ff0']
});
  }
});

</script>

<template>
  <div class="results">
    <p>Tu resultado...</p>
    <h1>{{ numberOfCorrectAnswer }}/{{ quizQuestionLength }}</h1>
    <div>
      <button class="again-btn">
      <RouterLink to="/" class="again">Vuelve a jugar</RouterLink>
    </button>
      <div
        v-if="numberOfCorrectAnswer === quizQuestionLength">
        <p class="congratulations">
          ¡Felicidades!<br />
          Has respondido a todas las preguntas correctamente
        </p>
      </div>
      <div v-else-if="numberOfCorrectAnswer === 0">
        <p class="better-luck">
          ¡No te desanimes! <br />Seguro que la próxima vez lo harás mejor
        </p>
      </div>
      <div v-else>
        <p class="better-luck">¡Bien hecho! Pero aún puedes mejorar</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.results {
  text-align: center;
  padding: 100px 0;
}
p {
  font-size: 35px;
}
h1 {
  font-size: 100px;
}
.again-btn {
  font-size: 24px;
  padding: 10px;
  background-color: lightblue;
  border: 2px solid black;
  border-radius: 10px;
  margin: 30px 30px;
}
.again {
  text-decoration: none;
  color: black;
}
.congratulations {
  font-size: 35px;
  color: #247a38;
  margin-bottom: 20px;
}
.better-luck {
  font-size: 30px;
  color: black;
  margin: 20px;
}
.results {
  position: relative;
  text-align: center;
}
</style>
