<script setup>
import { ref } from 'vue'

const message = ref('Hello World!')

//variable
const msg = 'Ssup!!'

//functions
function log() {
  console.log(msg)
}

</script>

<template>
  <h1>{{ message }}</h1>
  <div @click='log'>{{msg}}</div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>