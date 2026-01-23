<script setup lang="ts">
import { useRoute } from 'vue-router';
import { useTodoStore } from '../stores/todoStores';
const todoStore = useTodoStore()
const route = useRoute()
const id = Number(route.params.id)

</script>

<template>
    <section>
        <h2>Todo Details</h2>
        <div v-if="todoStore.todos[id - 1]">
        {{ todoStore.todos[id-1] }}
        </div>
    </section>
</template>