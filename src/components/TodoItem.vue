<template>
    <li>
      <span>{{ task.name }}</span>
      <button @click="deleteTask">Delete</button>
      <button @click="editTask">Edit</button>
    </li>
  </template>
  
  <script setup>
  const props = defineProps({
    task: Object,
  });
  
  function deleteTask() {
    emit('delete-task', props.task.id);
  }
  
  function editTask() {
    const newTaskName = prompt('Edit task name', props.task.name);
    if (newTaskName !== null) {
      emit('edit-task', props.task.id, newTaskName);
    }
  }
  </script>
  