<script setup>
  import QuizHeader from '@/components/QuizHeader.vue';
  import Question from '@/components/Question.vue';
  import { useRoute } from 'vue-router';
  import quizes from "../data/quizes.json"
  import { ref } from 'vue';
  import { computed } from 'vue';
  import Result from '@/components/Result.vue';
  

  const route = useRoute()
  const quizId = parseInt(route.params.id)
  const quiz = quizes.find(q => q.id === quizId)
  const currentQuestionIndex = ref(0)
  const numberOfCorrectAnswer = ref(0)
  const showResults = ref(false)
 

  const questionStatus = computed(() => `${currentQuestionIndex.value +1}/${quiz.questions.length}`)

  const barPercentage = computed(() =>
  `${currentQuestionIndex.value / quiz.questions.length * 100}%`)

  const onOptionSelected = (isCorrect) => {
    if(isCorrect) {
      numberOfCorrectAnswer.value++
    }
    if(quiz.questions.length -1 === currentQuestionIndex.value) {
      showResults.value = true
    }
    
    currentQuestionIndex.value++
  }
</script>

<template>
    <QuizHeader
      v-if="!showResults"
      :questionStatus="questionStatus"
      :barPercentage="barPercentage"/>
    <Question 
      v-if="!showResults"
      :question="quiz.questions[currentQuestionIndex]"
      @selectedOption="onOptionSelected"/>
    <Result 
      v-else
      :quizQuestionLength ="quiz.questions.length"
      :numberOfCorrectAnswer="numberOfCorrectAnswer"/>
    
</template>