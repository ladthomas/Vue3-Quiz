<template>
    <ul>
      <li v-for="answer in answers" :key="answer.id" @click="selectAnswer(answer)">
        {{ answer.title }}
      </li>
    </ul>
  </template>
  
  <script>
  export default {
    props: {
      answers: Array
    },
    methods: {
      selectAnswer(answer) {
        this.$emit('selected', answer)
      }
    }
  }
  </script>
  