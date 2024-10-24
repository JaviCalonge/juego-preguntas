<script setup>
import q from "../data/quizes.json"
import {ref, watch} from "vue"
import Card from "../components/Card.vue";

const quizes = ref(q)
const search = ref("")

watch(search, () => {
  quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})

</script>

<template>
  <div>
    <header class="title">
      <h1>Cuestionario</h1>
      <input v-model.trim="search" type="text" placeholder="Buscar..." />
    </header>
    <div class="option-container">
        <Card class="card" v-for="quiz in quizes" :key="quiz.id" :quiz="quiz"/>
    </div>
  </div>
</template>

<style scoped>
.title {
  margin-left: 50px;
}
.title h1 {
  font-size: 60px;
  margin-top: 30px;
}
.title input {
  height: 30px;
  width: 200px;
}
.option-container {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  margin-top: 40px;
}

@media (max-width: 1110px) {
  .title {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: 0;
}
  .title h1 {
    margin-top: 0;
  }
}
</style>
