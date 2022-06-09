<!--
This example fetches Vue.js commits data from GitHub’s API and displays them as a list.
You can switch between the two branches.
-->

<script setup>
import { ref, watchEffect } from 'vue'

const API_URL = `https://api.github.com/repos/vuejs/core/commits?per_page=3&sha=`
const branches = ['main', 'v2-compat']

const currentBranch = ref(branches[0])
const commits = ref(null)

watchEffect(async () => {
    //This effect runs immediately and then
    //re-run whenever currentBranch.value changes
    const url = `${API_URL}${currentBranch.value}`
    commits.value = await (await fetch(url)).json()
})

function truncate(v) {
    const newline = v.indexOf('\n')
    return newline > 0 ? v.slice(0, newline) : v
}

function formatDate(v) {
    return v.replace(/T|Z/g, ' ')
}

</script>

<template>
  <h1>Latest Vue Core Commits</h1>
  <div v-for="branch in branches" :key='branch.id'>
    <input type="radio"
      :id="branch"
      :value="branch"
      name="branch"
      v-model="currentBranch">
    <label :for="branch">{{ branch }}</label>
  </div>


</template>