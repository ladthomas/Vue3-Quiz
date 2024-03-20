<template>
    <div>
      <Question v-if="!showResults" :question="currentQuestion" @answer-selected="handleAnswer" />
      <Results v-else :score="score" :questions="questions" :userAnswers="userAnswers" />
    </div>
  </template>
  
  <script>
  import Question from './Question.vue'
  import Results from './Results.vue'
  import quizData from '../data/halloween.json'
  
  export default {
    components: {
      Question,
      Results
    },
    data() {
      return {
        questions: quizData,
        currentQuestionIndex: 0,
        userAnswers: [],
        score: 0,
        showResults: false,
      }
    },
    computed: {
      currentQuestion() {
        return this.questions[this.currentQuestionIndex]
      }
    },
    methods: {
      handleAnswer(isCorrect) {
        if (isCorrect) {
          this.score++
        }
        this.userAnswers.push({ question: this.currentQuestion.title, isCorrect })
        if (this.currentQuestionIndex < this.questions.length - 1) {
          this.currentQuestionIndex++
        } else {
          this.showResults = true
        }
      },
      restartQuiz() {
    this.currentQuestionIndex = 0;
    this.userAnswers = [];
    this.score = 0;
    this.showResults = false;
  }
    }
  }
  </script>
  