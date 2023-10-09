<template>
  <div id="quiz">
    <h1>Cognito Forms Quiz</h1>


    <div v-for="(question, index) in questions" :key="index">
      <Question :question="question"></Question>
    </div>
    <div>
      {{ `Question ${currentQuestion} of ${questions.length}` }}
    </div>
    <div v-if="showSummary">

    </div>
  </div>
</template>

<script>

import Question from '@/components/Question.vue';

export default {
  props: {
    questions: {
      type: Array,
      required: true
    }
  },
  components: {
    Question
  },
  data() {
    return {
      showSummary: false
    };
  },
  computed: {
  }
};

</script>

<style>

#quiz {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c2c4e;
  text-align: center;
}
</style>
