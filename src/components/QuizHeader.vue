<script setup>
  import { defineProps } from 'vue';

  const {questionStatus, barPercentage} = defineProps(["questionStatus", "barPercentage"])

</script>

<template>
  <header>
      <a href="/index.html"><h4>Pregunta {{ questionStatus }}</h4></a>
      <div class="bar">
        <div class="completion" :style="{width: barPercentage}"></div>
      </div>
    </header>
</template>

<style scoped>
header {
  margin-top: 20px;
  display: flex;
  align-items: center;
  gap: 20px;
}
header a {
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

@media (max-width: 1110px) {
  header {
  flex-direction: column;
}
}
</style>