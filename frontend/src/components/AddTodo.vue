<script setup lang="ts">  
import { ref } from 'vue';

type Todo = {id: number; title: string; completed: boolean };

const todos = defineModel<Todo[]>("todos", {required: true});



const newTitle = ref('');

const nextId = ref(Math.max(0, ...todos.value.map((t) => t.id)) + 1);

function addTodo() {
  const title = newTitle.value;
  todos.value.push({ id: nextId.value++, title, completed: false });
  newTitle.value = '';
}
</script>

<template>
  <section>
    <h2>New todo</h2>
    <div style="display: flex; align-items: center; gap: 0.5rem; margin-top: 0.25rem;">
      <input
       v-model="newTitle"
       placeholder="New todo title"
       aria-label="=New todo title"
      />
      <button v-on:click="addTodo" :disabled="!newTitle">Add</button>
    </div>
  </section>

</template>


