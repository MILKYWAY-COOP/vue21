<!--
This example fetches Vue.js commits data from GitHub’s API and displays them as a list.
You can switch between the two branches.
-->

<script setup>
import { ref, watchEffect } from 'vue';

const API_URL = `https://api.github.com/repos/vuejs/core/commits?per_page=3&sha=`;
const branches = ['main', 'v2-compat'];

const currentBranch = ref(branches[0]);
const commits = ref(null);

watchEffect(async () => {
  //This effect runs immediately and then
  //re-run whenever currentBranch.value changes
  const url = `${API_URL}${currentBranch.value}`;
  commits.value = await (await fetch(url)).json();
  console.log(await (await fetch(url)).json());
});

console.log(commits.value);
function truncate(v) {
  const newline = v.indexOf('\n');
  return newline > 0 ? v.slice(0, newline) : v;
}

function formatDate(v) {
  return v.replace(/T|Z/g, ' ');
}

</script>

<template>
  <h1>Latest Vue Core Commits</h1>
  <div v-for="branch in branches" :key="branch.id">
    <input
      type="radio"
      :id="branch"
      :value="branch"
      name="branch"
      v-model="currentBranch"
    />
    <label :for="branch">{{ branch }}</label>
  </div>
  <p>vuejs/vue@{{ currentBranch }}</p>
  <ul>
    <li v-for="{ html_url, sha, author, commit } in commits" :key="sha.id">
      <a :href="html_url" target="_blank" class="commit">
        {{ sha.slice(0, 7) }}
      </a>
      - <span class="message">{{ truncate(commit.message) }}</span
      ><br />
      by
      <span class="author">
        <a :href="author.html_url" target="_blank">{{ commit.author.name }}</a>
      </span>
      at <span class="date">{{ formatDate(commit.author.date) }}</span>
    </li>
  </ul>
</template>

<style>
body {
    background-color: beige;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

h1 {
    color: chocolate;
}

a {
  text-decoration: none;
  color: #42b883;
}
li {
  line-height: 1.5em;
  margin-bottom: 20px;
}
.author,
.date {
  font-weight: bold;
}
</style>
