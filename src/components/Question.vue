<template>
    <div>
      <h2>{{ question.title }}</h2>
      <Answers :answers="question.answers" @selected="answerSelected" />
    </div>
  </template>
  
  <script>
  import Answers from './Answers.vue'
  
  export default {
    components: {
      Answers
    },
    props: {
      question: Object
    },
    methods: {
      answerSelected(answer) {
        this.$emit('answer-selected', answer.correct)
      }
    }
  }
  </script>
  