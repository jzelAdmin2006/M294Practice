<script setup>
import { ref, computed } from 'vue'

const inputText = ref('')
const inputEstimation = ref(0)
const highPriorityInput = ref(false)

const tasks = ref([
  { high_priority: false, text: 'Rasen mähen', estimation: 2, done: true },
  { high_priority: true, text: 'Französisch lernen', estimation: 4, done: false },
  { high_priority: true, text: 'Einkaufen', estimation: 8, done: false },
  { high_priority: true, text: 'Abfall rausbringen', estimation: 16, done: false },
])

const sortedTasksByPriority = computed(() => {
  return tasks.value.sort((a, b) => {
    return a.high_priority === b.high_priority ? 0 : a.high_priority ? -1 : 1
  })
})

function add() {
  tasks.value.push({
    text: inputText.value,
    done: false,
    high_priority: highPriorityInput.value,
    estimation: inputEstimation.value,
  })

  highPriorityInput.value = false
  inputText.value = ''
  inputEstimation.value = 0
}

function deleteTask(index) {
  tasks.value.splice(index, 1)
}
</script>

<template>
  <div class="container">
    <h2>
      Aufgabenliste
    </h2>
    
    <p>
      {{ tasks.filter(task => task.done).length }} von {{ tasks.length }} Tasks sind erledigt
    </p>

    <div class="form-group">
      <label for="task">Neuer Task</label>
      <input class="form-control" id="task" type="text" v-model="inputText">
    </div>

    <div class="form-group">
      <label for="estimation">Aufwandschätzung in Stunden</label>
      <input class="form-control" id="estimation" type="number" v-model="inputEstimation">
    </div>

    <label for="prio">
      <input id="prio" type="checkbox" v-model="highPriorityInput">
      Hohe Priorität
    </label>

    <div class="form-actions">
      <button @click="add">
        Task hinzufügen
      </button>
    </div>
    
    <ul>
      <li v-for="task, index in sortedTasksByPriority" v-bind:class="{'is-done':task.done, 'high-priority':task.high_priority}">
        <input id="done" type="checkbox" v-model="task.done">
        {{ task.text }}
        ({{ task.estimation }})
        <button @click="deleteTask(index)">Löschen</button>
      </li>
    </ul>
  </div>
</template>

<style>
  .is-done {
    text-decoration: line-through;
  }
  
  .high-priority {
    font-weight: bold;
    color: red;
  }
  
  .form-group {
    display: block;
  }
  
  .form-group label {
    display: block;
    margin-bottom: 2px;
  }
  
  .form-control {
    width: 100%;
    padding: 2px 5px;
    height: 32px;
    margin-bottom: 5px;
  }
  
  .form-actions {
    display: block;
    margin-top: 1rem;
    margin-bottom: 2rem;
  }
  
  .container {
    margin: 20px auto;
    max-width: 400px;
    width: 100%;
  }
</style>