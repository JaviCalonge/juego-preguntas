<script setup>
  import { defineProps, defineEmits } from 'vue';

  const emit = defineEmits(["selectedOption"])

  const {question} = defineProps(["question"])

  const emitSelectedOption = (isCorrect) => {
    emit("selectedOption", isCorrect)
  }
</script>

<template>
    <div class="question-container">
      <h1 class="question">{{ question.text }}</h1>
    </div>
    <div class="options-container">
      <div v-for="option in question.options" :key="option.id" class="option" @click="emitSelectedOption(option.isCorrect)">
        <p class="option-label">{{ option.label }}</p>
        <div class="option-value">
          <p>{{ option.text }}</p>
        </div>
      </div>
    </div>
</template>

<style scoped>
.question-container {
  margin-top: 20px;
}
.question {
  font-size: 40px;
  margin-bottom: 20px;
}
.option {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
  cursor: pointer;
}
.option-label {
  background-color: lightblue;
  width: 50px;
  height: 50px;
  font-size: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.option-value {
  background-color: white;
  width: 100%;
  font-size: 30px;
  padding: 0 20px;
}

@media (max-width: 1110px) {
  .question-container {
    margin: 50px;
}
  .question {
    font-size: 26px;
    margin: 0;
}
  .options-container {
    margin: 0 50px;
}
  .option-value {
    background-color: white;
    width: 100%;
    font-size: 18px;
    padding: 8px 10px;
}
}
</style>