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

const handleSubmit = () => {
  if (selected.value === questions[0].answer){
    correct.value = true
  } else {
    correct.value = false
  }
}

</script>
<template>
  <div class="flex items-center justify-center h-screen">
    <div>
      <ul>
        <li class="text-white font-bold">
          {{ questions[0].question }}
          <hr/>
          <ul class="mt-0.5">
            <li v-for="option in questions[0].options">
              <input type="radio" :value="option" v-model="selected"/>
              <label>{{option}}</label>
            </li>
          </ul>
          <div class="mt-3">
            <button @click="handleSubmit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
              Submit
            </button>
            <p v-if="correct === true" class="text-green-400">Correct!</p>
            <p v-if="correct === false" class="text-red-400">incorrect!</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>
