<template>
    <div id="quiz">
        <h1>Cognito Forms Technical Exercise</h1>
        <div class="quiz-container">
            <Question
                :key=questionIndex
                :question="questions[questionIndex]"
                :questionIndex="questionIndex"
                :responses="responses" 
                @selectAnswer="selectAnswer"
            >
            </Question>
            <div>
                {{ `Question ${questionIndex + 1} of ${questions.length}` }}
            </div>
        </div>
        <div>
            <button
                class="btn btn-next"
                v-if="questionIndex + 1 < questions.length"
                :disabled="isNavigationDisabled"
                :class="{ 'btn-disabled': isNavigationDisabled }"
                @click="next()"
            >
                {{ 'Next Question' }}
            </button>
            <button
                class='btn btn-summary'
                v-else @click="showSummary = true"
                :disabled="isNavigationDisabled"
                :class="{ 'btn-disabled': isNavigationDisabled }"
            >
                {{ 'See Summary' }}
            </button>
        </div>
        <Summary
            v-show="showSummary"
            :questions="questions"
            :responses="responses"
            @close="showSummary = false"
            @restart="restartQuiz"
        ></Summary>
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

        restartQuiz() {
            window.location.reload();
        },

        selectAnswer(answer) {
            this.$set(this.responses, this.questionIndex, answer);
            this.isNavigationDisabled = false;
        }
    }
};

</script>

<style>
#quiz {
    font-family: Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c2c4e;
    text-align: center;
}

.quiz-container {
    margin: 3rem auto;
    max-width: 75%;
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
    min-width: 250px;
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
    color: rgba(0, 0, 0, 0.2);

    &:hover {
        background-color: rgba(0, 0, 0, 0.05);
    }
}
</style>
