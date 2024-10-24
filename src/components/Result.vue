<script setup>
  import { defineProps } from 'vue';
  import { RouterLink } from 'vue-router';

  const {quizQuestionLength, numberOfCorrectAnswer} = defineProps(["quizQuestionLength","numberOfCorrectAnswer"])
</script>

<template>
  <div class="results">
    <p>Your results...</p>
    <h1>
      {{ numberOfCorrectAnswer }}/{{ quizQuestionLength }}
    </h1>
    
    <div v-if="numberOfCorrectAnswer === quizQuestionLength" class="confetti-container">
      <span v-for="n in 50" :key="n" class="confetti">🎉</span>
      <span v-for="n in 10" :key="n" class="confetti">⭐</span>
      
    </div>

    <button class="again-btn">
      <RouterLink to="/" class="again">Try another quiz!</RouterLink>
    </button>
  </div>
</template>


<!-- <template>
  <div class="results">
    <p>Your results...</p>
    <h1>
      {{ numberOfCorrectAnswer }}/{{ quizQuestionLength }}
    </h1>
  
    <div v-if="numberOfCorrectAnswer === quizQuestionLength" class="congratulations">
      🎉 ¡Felicidades! 🎉 <br> Has respondido a todas las preguntas correctamente
    </div>

    
    <div v-else class="better-luck">
      ¡Bien hecho! Pero aún puedes mejorar
    </div>
    <button class="again-btn">
    <RouterLink to="/" class="again">Try another quiz!</RouterLink>
  </button>
  </div>
</template> -->

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
  margin-top: 20px;
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

.confetti-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  pointer-events: none;
  overflow: hidden;
}

.confetti {
  position: absolute;
  top: -10%;
  font-size: 2rem;
  animation: fall 4s linear infinite;
  opacity: 0;
}

@keyframes fall {
  0% {
    transform: translateY(-100vh);
    opacity: 1;
  }
  100% {
    transform: translateY(100vh);
    opacity: 1;
  }
}

.confetti:nth-child(1n) {
  left: 10%;
  animation-duration: 4s;
}

.confetti:nth-child(2n) {
  left: 30%;
  animation-duration: 6s;
}

.confetti:nth-child(3n) {
  left: 50%;
  animation-duration: 5s;
}

.confetti:nth-child(4n) {
  left: 70%;
  animation-duration: 8s;
}

.confetti:nth-child(5n) {
  left: 90%;
  animation-duration: 7s;
}

.confetti:nth-child(6n) {
  left: 15%;
  animation-duration: 4.5s;
}

.confetti:nth-child(7n) {
  left: 35%;
  animation-duration: 5.5s;
}

.confetti:nth-child(8n) {
  left: 55%;
  animation-duration: 6.5s;
}

.confetti:nth-child(9n) {
  left: 75%;
  animation-duration: 4.8s;
}

.confetti:nth-child(10n) {
  left: 95%;
  animation-duration: 6.2s;
}
</style>