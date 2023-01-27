<template>
    <div class="results">
        <p>Yout Results...</p>
        <h1>{{numberOfCorrectAnswers}}/{{quizQuestionLength}}</h1>
        <RouterLink to="/">Go back</RouterLink>
    </div>
</template>

<script setup>
import { RouterLink } from 'vue-router';

const {numberOfCorrectAnswers, quizQuestionLength} = defineProps(["quizQuestionLength", "numberOfCorrectAnswers"])
</script>

<style scoped>
.results{
    text-align: center;
    padding: 100px 0;
}
p{
    font-size: 25px;
}
h1{
    font-size: 80px;
}
</style>