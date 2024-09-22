<template>
  <div class="container">
    <h1>My To-Do List</h1>
    <TodoForm @add-task="addTask" />
    <ul>
      <TodoItem
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @delete-task="deleteTask"
        @edit-task="editTask"
      />
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TodoForm from './components/TodoForm.vue';
import TodoItem from './components/TodoItem.vue';

const tasks = ref([]);
let nextId = 1;

function addTask(taskName) {
  tasks.value.push({ id: nextId++, name: taskName });
}

function deleteTask(taskId) {
  tasks.value = tasks.value.filter(task => task.id !== taskId);
}

function editTask(taskId, newTaskName) {
  const task = tasks.value.find(t => t.id === taskId);
  if (task) {
    task.name = newTaskName;
  }
}
</script>

<style src="./assets/style.css"></style>
