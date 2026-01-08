<script setup lang="ts">
import AddTodo from './components/AddTodo.vue';
import { useTodoStore } from './stores/todoStores';


import { ListFormat } from 'typescript';
import { ref, computed } from 'vue';
const name = ref('Vue 3 with TypeScript');

const todoStore = useTodoStore();


</script>

<template>
  <div id="app">
    <h2>Todos</h2>

    <ul>
      <li
        v-for="todo in todoStore.todos"
        :key="todo.id"
        style="display:flex; align-items:center; gap:0.5rem; margin:0.25rem 0;"
      >
        <input type="checkbox" v-model="todo.completed" />
        <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
          {{ todo.title }}
        </span>
        <button v-on:click="todoStore.removeTodo(todo.id)">Delete</button>
      </li>
    </ul>

    <AddTodo />

  </div>



</template>