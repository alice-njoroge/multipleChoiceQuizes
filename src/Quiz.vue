<script setup>
import {ref} from "vue";

const questions = [
  {
    question: "What is the capital of France?",
    options: ["London", "Berlin", "Paris", "Rome"],
    answer: "Paris",
  },
  {
    question: "Which planet is closest to the sun?",
    options: ["Earth", "Mars", "Venus", "Mercury"],
    answer: "Mercury",
  },
  // Add more questions as needed
];
const page = ref(0);
const correct = ref();
const selected = ref('');
const completed = ref(false)

const reset = () => {
  selected.value = '';
  correct.value = null;
  if (page.value < questions.length - 1){
    page.value += 1
  }
  else{
    completed.value = true
  }
}

const handleSubmit = () => {
  if (selected.value === questions[page.value].answer) {
    correct.value = true
    reset();
  } else {
    correct.value = false
  }
}

</script>
<template>
  <div class="flex items-center justify-center h-screen">
    <div class="text-white font-bold" v-if="completed === false">
      {{ questions[page].question }}
      <hr/>
      <ul class="mt-0.5">
        <li v-for="option in questions[page].options" :key="option.answer">
          <input type="radio" :value="option" v-model="selected"/>
          <label>{{ option }}</label>
        </li>
      </ul>
      <div class="mt-3">
        <button @click="handleSubmit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
          {{ correct ? 'Next' : 'Submit' }}
        </button>
        <p v-if="correct === true" class="text-green-400">Correct!</p>
        <p v-if="correct === false" class="text-red-400">incorrect!</p>
      </div>
    </div>
    <div v-else class="text-white font-bold" >
      <p> Questions completed </p>
    </div>
  </div>
</template>
