<template>
  <div id="quiz">
    <h1>Cognito Forms Quiz</h1>
    <div class="quiz-container">
      <Question :key=questionIndex :question="questions[questionIndex]" :questionIndex="questionIndex"
        :responses="responses" @selectAnswer="selectAnswer">
      </Question>
      <div>
        {{ `Question ${questionIndex + 1} of ${questions.length}` }}
      </div>
    </div>
    <div>
      <button class="btn btn-next" v-if="questionIndex + 1 < questions.length" :disabled="isNavigationDisabled" :class="{'btn-disabled': isNavigationDisabled}" @click="next()">
        {{ 'Next Question' }}
      </button>
      <button class='btn btn-summary ' v-else @click="showSummary = true">
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
      responses: {},
      isNavigationDisabled: true
    };
  },

  computed: {
  },

  methods: {
    next() {
      this.isNavigationDisabled = true;
      if (this.questionIndex < this.questions.length - 1) {
        this.questionIndex++;
      }
    },

    selectAnswer(answer) {
      this.responses[this.questionIndex] = answer;
      this.isNavigationDisabled = false;
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

.quiz-container {
  margin: 1rem auto;
  padding: 1rem;
  max-width: 750px;
}

.btn {
    border: transparent 1px solid;
    border-radius: 20px;
    border-color: #42b883;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    transition-duration: 0.4s;
    cursor: pointer;
    width: 20%;
}

.btn-next {
    background-color: #ffffff;
    color: #2c2c4e;

    &:hover {
        background-color: rgba(0, 0, 0, 0.05);
    }
}

.btn-summary {
    border: none;
    background-color: #42b883;
    color: #ffffff;

    &:hover {
        background-color: rgba(66, 184, 131, 0.7);
    }
}

.btn-disabled {
    background-color: rgba(0, 0, 0, 0.05);
    border-color: rgba(0, 0, 0, 0.1);
    color: rgba(0, 0, 0, 0.2)
}
</style>
