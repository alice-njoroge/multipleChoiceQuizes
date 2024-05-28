<script setup>
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
</script>
<template>
  <div class="flex items-center justify-center h-screen">
    <ul>
      <li class="text-white font-bold">
        {{ questions[0].question }}
        <hr/>
        <ol class="list-disc mt-0.5">
          <li v-for="option in questions[0].options">
            {{option}}
          </li>
          </ol>
      </li>
    </ul>
  </div>
</template>
