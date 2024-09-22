<template>
    <div>
      <input v-model="newTask" placeholder="Add a new task" />
      <button @click="submitTask">Add Task</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const newTask = ref('');
  
  function submitTask() {
    if (newTask.value.trim() !== '') {
      emit('add-task', newTask.value);
      newTask.value = '';
    }
  }
  </script>
  