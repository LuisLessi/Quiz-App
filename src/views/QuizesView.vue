<template>
    <div class="container">
      <header>
        <h1>Quizes</h1>
        <input v-model.trim="search" type="text" placeholder="search...">
  
      </header>
      <div class="options-container">
        <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
        <!-- */<div v-for="quiz in quizes" :key="quiz.id" class="card">
          <img :src="quiz.img" alt="">
          <div class="card-text">
            <h2>{{ quiz.name }}</h2>
            <p>{{ quiz.questions.length }} questions</p>
          </div>
        </div>-->
      </div>
    </div>
  </template>
  
  <script setup>
  import q from "../data/quizes.json"
  import Card from "../components/Card.vue"
  import { ref, watch } from "vue"
  
  const quizes = ref(q)
  const search = ref("")
  
  watch(search, () => {
    quizes.value = q.filter(quiz => quiz.name.toLocaleLowerCase().includes(search.value.toLocaleLowerCase()))
  })
  </script>
  
  <style scoped>
  .container {
    max-width: 1000px;
    margin: 0 auto;
  }
  
  header {
    margin-bottom: 10px;
    margin-top: 30px;
    display: flex;
    align-items: center;
  }
  
  header h1 {
    font-weight: bold;
    margin-right: 30px;
  }
  
  header input {
    border: none;
    background-color: rgba(128, 128, 120, 0.1);
    border-radius: 5px;
    padding: 10px;
  }
  
  .options-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 4px;
  
  }
  
  /* CARD */
  
  .card {
    width: 310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
  }
  
  .card img {
    width: 100%;
    height: 190px;
    margin: 0;
  }
  
  .card .card-text {
    padding: 0 5px;
  }
  
  .card .card-text h2 {
    font-weight: bold;
  }
  </style>