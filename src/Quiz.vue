<template>
  <div id="quiz">
    <h1>Cognito Forms Quiz</h1>
    <Question :question="questions[questionIndex]" @selectAnswer="selectAnswer"></Question>
    <div>
      {{ `Question ${questionIndex + 1} of ${questions.length}` }}
    </div>
    <div>
      <button v-if="questionIndex + 1 < questions.length" @click="next()">
        {{ 'Next Question' }}
      </button>
      <button v-else @click="showSummary = true">
        {{ 'See Summary' }}
      </button>
    </div>
    <Summary v-show="showSummary" :responses="responses" @close="showSummary = false">

    </Summary>
  </div>
</template>
<script>

import Question from '@/components/Question.vue';
import Summary from '@/components/Summary.vue';

export default {
  props: {
    questions: {
      type: Array,
      required: true
    }
  },

  components: {
    Question,
    Summary
  },

  data() {
    return {
      showSummary: false,
      questionIndex: 0,
      responses: {}
    };
  },

  computed: {
  },

  methods: {
    next() {
      if (this.questionIndex < this.questions.length - 1) {
        this.questionIndex++;
      }
    },

    selectAnswer(answer) {
      this.responses[this.questionIndex] = answer;
      console.log(this.responses);
    }
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
