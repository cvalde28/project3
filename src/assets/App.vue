<template>
  <div class="container">
    <h1>Countdown Timer</h1>
    <div id="timerDisplay">{{ timer }}</div>
    <input type="number" v-model="minutes" placeholder="Minutes" />
    <button @click="startTimer">Start</button>
    <button @click="resetTimer">Reset</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const timer = ref('00:00:00');
const minutes = ref(0);
let timerInterval = null;

const startTimer = () => {
  if (minutes.value > 0) {
    let timeLeft = minutes.value * 60;
    timerInterval = setInterval(() => {
      const mins = Math.floor(timeLeft / 60);
      const secs = timeLeft % 60;
      timer.value = `${mins}:${secs < 10 ? '0' : ''}${secs}`;
      timeLeft--;
      if (timeLeft < 0) {
        clearInterval(timerInterval);
        timer.value = '00:00:00';
      }
    }, 1000);
  }
};

const resetTimer = () => {
  clearInterval(timerInterval);
  timer.value = '00:00:00';
};
</script>

<style scoped>
/* Add a border and some padding */
.container {
    border: 2px solid #007BFF;
    padding: 30px;
    border-radius: 10px;
    text-align: center;
}

/* Style the timer display */
#timerDisplay {
    font-size: 24px;
    margin-top: 20px;
    color: #FF5733;
}

/* Style the input field */
input[type="number"] {
    padding: 8px;
    font-size: 16px;
    width: 80px;
    text-align: center;
    margin-right: 10px; /* Space between input and button */
}

/* Style the buttons */
button {
    padding: 10px 20px;
    font-size: 16px;
    margin: 5px;
    cursor: pointer;
    border: none;
    border-radius: 5px;
    background-color: #007BFF;
    color: white;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #0056b3;
}
</style>
