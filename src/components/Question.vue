<template>
    <div>
        <div class="question">
            <span>
                {{ question.text }}
            </span>
        </div>
        <button class="option" v-for="(option, index) in question.answers" :key="index" @click="$emit('selectAnswer', question.answers[index])">
            {{ option }}
        </button>


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