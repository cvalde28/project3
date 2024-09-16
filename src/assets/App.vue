<template>
  <div class="container">
    <h1>To-Do List</h1>
    <input v-model="newTask" placeholder="New Task" />
    <button @click="addTask">Add Task</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const newTask = ref('');
const tasks = ref([]);

const addTask = () => {
  if (newTask.value.trim()) {
    tasks.value.push(newTask.value.trim());
    newTask.value = '';
  }
};
</script>

<style>
.container {
  width: 300px;
  margin: 0 auto;
}

input, button {
  margin: 10px 0;
  padding: 8px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  background: #f0f0f0;
  margin: 5px 0;
  padding: 10px;
}
</style>
