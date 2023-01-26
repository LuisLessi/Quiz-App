<template>
    <div>
        {{ barPercentage }}
        <QuizHeader :questionStatus = "questionStatus"
        :barPercentage="barPercentage"/>
    </div>
    <div>
        <Question :question="quiz.questions[currentQuestionIndex]"/>
    </div>
    <button @click="currentQuestionIndex++">Next Question</button>
</template>

<script setup>
import { useRoute } from "vue-router";
import { ref, watch, computed } from "vue";
import quizes from "../data/quizes.json"
import Question from "../components/Question.vue"
import QuizHeader from "../components/QuizHeader.vue"

const route = useRoute()

const quizId = parseInt(route.params.id)

const currentQuestionIndex = ref(0)

const quiz = quizes.find(q => q.id === quizId)

//const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)

/**watch(() => currentQuestionIndex.value, () => {
    questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`
}) **/

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const barPercentage = computed(() => `${currentQuestionIndex.value/quiz.questions.length * 100}%`)
</script>

<style>

</style>