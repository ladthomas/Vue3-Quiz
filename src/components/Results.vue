<template>
    <div class="results">
      <h2>Résultats</h2>
      <p>Score : {{ score }} / {{ questions.length }}</p>
      <ul>
        <li v-for="(userAnswer, index) in userAnswers" :key="index">
          <p>Question {{ index + 1 }}: {{ questions[index].title }}</p>
          <p>Votre réponse: {{ userAnswer.isCorrect ? 'Correcte' : 'Incorrecte' }}</p>
          <p v-if="!userAnswer.isCorrect">
            Réponse correcte: {{ findCorrectAnswer(questions[index].answers) }}.
          </p>
        </li>
      </ul>
      <button @click="restartQuiz">Recommencer le Quiz</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      score: Number,
      questions: Array,
      userAnswers: Array,
    },
    methods: {
      findCorrectAnswer(answers) {
        const correctAnswer = answers.find(answer => answer.correct);
        return correctAnswer ? correctAnswer.title : 'Information manquante';
      },
      restartQuiz() {
        this.$emit('restart-quiz');
      },
    },
  };
  </script>
  
  <style scoped>
  /* Ajoutez ici vos styles spécifiques au composant Results */
  .results {
    text-align: left;
    max-width: 600px;
    margin: auto;
  }
  </style>
  