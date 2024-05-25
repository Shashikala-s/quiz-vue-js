<script setup>

import {ref,computed}  from 'vue'
const questions =ref([
  
{
  question:"what is Vue ?",
  answer: 0,
  option:[
    'A',
    'B',
    'C'
  ]
},
{
  question:"what is this ?",
  answer: 0,
  option:[
    'A',
    'B',
    'C'
  ]
},{
  question:"what is be ?",
  answer: 0,
  option:[
    'A',
    'B',
    'C'
  ]
},
])

const quizCompleted=ref(false)
const currentQuestion=ref(0)
const score=computed(()=>{

  let value=0
  questions.value.map(q =>{
    if(q.selected==q.answer){
      value++
    }
  })
  return value
})

const getCurrentQuestion=computed(()=>{
  let question=questions.value[currentQuestion.value]
  question.index=currentQuestion.value
  return question
})

const setAnswer=evt =>{
  questions.value[currentQuestion.value].selected=evt.taregt.value
evt.taregt.value=null
}

const nextQuestion=()=>{
  if(currentQuestion.value<questions.length-1){
    currentQuestion.value++
  }else{
    quizCompleted.value==true
  }
}
</script>
<template>
  <main class="app">
  </main>  <h1>Quiz</h1>
  <section class=""quiz>
    <div class=""quiz-info>
      <span class="question">{{ getCurrentQuestion.question }}</span>
      <span class="question">{{ score }}/{{ questions.length }}</span>
   
      <div class="option">
        <label>
          <input type="radio"
          :name="getCurrentQuestion.index"
          :value="index">
        </label>
      </div>
    </div>
  </section>
</template>


<style>
*{
  margin: 0;
  padding: auto;
}
</style>

