<!-- Here we show the simplest possible component which accepts a prop
and renders it.  -->
<script setup>
import { ref } from 'vue'
import TodoItem from './TodoItem.vue'
import TodoItem from './TodoItem.vue';

const groceryList = ref([
  {id: 0, text: 'Vegetables'},
  {id: 1, text: 'Cheese'},
  {id: 2, text: 'Whatever else humans are supposed to eat'},
])
</script>

<template>
  <ol>
  <TodoItem />
  </ol>
</template>