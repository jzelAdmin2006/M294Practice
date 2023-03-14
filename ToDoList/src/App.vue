<script setup>
import { ref } from 'vue'
  const todos = ref([
    { task: "Vue.js lernen", done: true },
    { task: "Franz lernen", done: true },
    { task: "An Plänen zur Weltherrschaft arbeiten", done: false },
    { task: "Katzenklo reinigen", done: false }
  ])
</script>

<template>
  <h1>Todo - Listen anzeigen</h1>
  <div v-for="todo in todos">
    <input type="checkbox" v-model="todo.done"/> {{ todo.task }} <span v-if="todo.done">🎉</span>
  </div>
</template>

<style>
  body {
    font-family: Arial, Helvetica, sans-serif;
  }
</style>