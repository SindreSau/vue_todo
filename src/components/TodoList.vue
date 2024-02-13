<script setup>
import TodoItem from './TodoItem.vue'
import { ref, onMounted } from 'vue'

// Set focus to input on load
onMounted(() => {
  document.querySelector('input').focus()
  if (localStorage.getItem('tasks')) {
    tasks.value = JSON.parse(localStorage.getItem('tasks'))
  }
})

let tasks = ref([])
let task = ref('')

const addTask = () => {
  if (!task.value) return
  tasks.value.push(task.value)
  localStorage.setItem('tasks', JSON.stringify(tasks.value))
  task.value = ''
}
</script>

<template>
  <form @submit.prevent="addTask" action="">
    <input v-model="task" type="text" placeholder="What do you need to do?" />
    <button type="submit">Add</button>
  </form>
  <ul>
    <TodoItem v-for="(todo, index) in tasks" :key="index" :todo="todo" />
  </ul>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: row;
  gap: 30px;
  margin-bottom: 10px;
}

form input,
button {
  padding: 10px;
}

form button {
  border-radius: 10px;
  padding-inline: 30px;
  border: none;
  background-color: #8b9ac6;
  color: white;
  cursor: pointer;
  transition: background-color 0.2s;
}

form button:hover {
  background-color: #6c7abf;
}

form input {
  /* INPUT RESET */
  outline: none;
  border: none;

  flex: 1;
  background: transparent;
  color: white;
  border-bottom: 1px solid white;
}

form input:focus {
  border-bottom: 1px solid #8b9ac6;
}

ul {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 0;
}
</style>
