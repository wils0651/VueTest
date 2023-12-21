<script setup>
import { ref, watchEffect } from 'vue'

const API_URL = `https://localhost:44348/api/TodoItems`

const todoItems = ref(null)

watchEffect(async () => {
  // this effect will run immediately 
  const url = `${API_URL}`
  todoItems.value = await (await fetch(url)).json()
  console.log('data we got', todoItems)
})

</script>

<template>
    <h1>Get Some Data</h1>
    <ul>
      <li v-for="{ id, name, isComplete } in todoItems">
        <span class="message">{{ id }}</span> 
        name <span class="author">{{ name }}</span>
      </li>
    </ul>
  </template>
