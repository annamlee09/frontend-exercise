<template>
    <div>
        <h2>
            {{ question.text }}
        </h2>
        <div class="options">
            <button class="btn-option" v-for="(option, index) in question.answers" :key="index" @click="selectAnswer(index)"
                :class="{ 'is-selected': answerIndex === index + 1 }">
                {{ option }}
            </button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'question',
    data() {
        return {
            answerIndex: 0
        };
    },
    props: ['question', 'questionIndex', 'responses'],
    methods: {
        selectAnswer(index) {
            this.$emit('selectAnswer', this.question.answers[index]);
            this.answerIndex = index + 1;
        }
    }

}
</script>

<style scoped>
.question {
    font-size: 18px;
}

.options {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
}

.btn-option {
    background-color: rgba(0, 0, 0, 0.05);
    border: none;
    border-radius: 20px;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    transition-duration: 0.4s;
    cursor: pointer;
    width: 20%;

    &:hover {
        background-color: rgba(0, 0, 0, 0.1);
    }

    &.is-selected {
        background-color: #42b883;
        color: #ffffff;
    }
}
</style>