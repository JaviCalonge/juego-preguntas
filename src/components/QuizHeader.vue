<script setup>
  import { defineProps } from 'vue';

  const {questionStatus, barPercentage} = defineProps(["questionStatus", "barPercentage"])

</script>

<template>
  <header>
    <div>
      <h4>Pregunta {{ questionStatus }}</h4>
      <div class="bar">
        <div class="completion" :style="{width: barPercentage}"></div>
      </div>
    </div>
      <RouterLink to="/"><button class="back">Vover</button></RouterLink>
    </header>
</template>

<style scoped>
header {
  margin-top: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}
header h4 {
  text-decoration: none;
  font-size: 30px;
  font-weight: bold;
  color: black;
}
.bar {
  width: 300px;
  height: 40px;
  border: 3px solid black;
  background-color: white;
}
.completion{
  height: 100%;
  width: 0;
  background-color: lightblue;
}
.back {
  margin-top: -20px;
  font-size: 24px;
  padding: 10px;
  background-color: lightblue;
  border: 2px solid black;
  border-radius: 10px;
}

@media (max-width: 1110px) {
  header {
  justify-content: space-evenly;
}
  .back {
    margin: 0;
    font-size: 14px;
    padding: 6px;
    background-color: lightblue;
    border: 2px solid black;
    border-radius: 10px;
}
}
</style>