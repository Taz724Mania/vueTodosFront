<template>
  <div>
    <h1>To Do:</h1>
    <button>Add to Your List</button>
    <ul>
      <li v-for="todo in todos" v-bind:key="todo._id">
        <h2>{{ todo.subject }}</h2>
        <h3>{{ todo.details }}</h3>
        <h3>{{ todo.dueDateTime }}</h3>
        <h4>{{ todo.completed }}</h4>
      </li>
    </ul>
  </div>
</template>

<script setup>
import {ref, onBeforeMount} from 'vue'

  const url = "https://vuetodos.onrender.com/todos"
  const todos = ref([])

  const getTodos = async function() {
    const response = await fetch (url)
    const data = await response.json()
    todos.value = data
  }

  onBeforeMount(() => {getTodos()})
</script>

<style>

</style>