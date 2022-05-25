<script setup>
import { ref } from 'vue';

const message = ref('Stephen Maina');

function reverseMessage() {
  message.value = message.value.split('').reverse().join('');
}

function notify() {
  alert('Navigation was prevented.')
}
</script>

<template>
  <!-- we do not need .value inside templates because 
  refs are automatically "unwrapped" in templates -->
  <h1>{{ message }}</h1>

  <!-- Bind to a method/function. The @click syntax is
  short for v-on click -->
  <button @click="reverseMessage">Reverse Message</button>

  <!-- Vue caters for inline expression statements -->
  <button @click="message += '!'">Append "!"</button>

  <!--Vue also provides modifiers for common tasks such as e.preventDefault()
  and e.stopPropagation()-->
  <a href="https://vuejs.org" target="blank" @click.prevent="notify"
    >Link 1. Visit vuejs.org</a
  >
  <a href="https://vuejs.org">Link 2. Visit vuejs.org</a>
  <hr />
</template>

<style>
body {
  background-color: antiquewhite;
  display: flex;
  align-items: center;
  flex-direction: column;
}

h1 {
  color: rgb(6, 2, 36);
  font-size: 70px;
  font-weight: 600;
  font-family: cursive;
  background-clip: text;
  -webkit-background-clip: text;
}

button {
  height: 50px;
  align-self: center;
  margin-left: 200px;
  border-radius: 10px;
  width: 90px;
  background-color: brown;
  border: 1px solid black;
}

button:hover {
  background-color: black;
  color: brown;
}

button,
a {
  display: block;
  margin-bottom: 1em;
}

a {
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  margin-left: 150px;
  text-decoration: underline;
}
</style>
