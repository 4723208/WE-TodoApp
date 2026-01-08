<script setup lang="ts">  
import { useTodoStore } from '@/stores/todoStores';
import { ref } from 'vue';

const todoStore = useTodoStore();

const newTitle = ref<string>('');

function addTodo(){
    todoStore.addTodo(newTitle.value);
    newTitle.value = '';
}

</script>

<template>
  <section>
    <h2>New todo</h2>
    <div style="display: flex; align-items: center; gap: 0.5rem; margin-top: 0.25rem;">
      <input type="text" v-model="newTitle" placeholder="New todo title" aria-label="=New todo title"/>
      <button v-on:click="todoStore.addTodo(newTitle)" :disabled="!newTitle">Add</button>
    </div>
  </section>

</template>


