<template>
    <div>
        <div class="question">
            <span>
                {{ question.text }}
            </span>
        </div>
        <form>
            <button class="answer" v-for="(answer, index) in question.answers" :key="index">
                {{ answer }}
            </button>
        </form>

    </div>
</template>

<script>

export default {
    name: 'question',
    data() {
        return {

        };
    },
    props: ['question']
}
</script>

<style scoped>
.question {
    font-size: 18px;
}
</style>