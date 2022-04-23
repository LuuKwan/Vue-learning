<script setup>
import { ref, computed, watchEffect } from "vue";

const props = defineProps({
  msg: {
    type: String,
    required: true,
  },
});

const API_URL = `https://api.github.com/repos/vuejs/core/commits?per_page=3&sha=`;
const branches = ["main", "v2-compat"];

const currentBranch = ref(branches[0]);
const commits = ref(null);

const watchBranch = watchEffect(async () => {
  const url = `${API_URL}${currentBranch.value}`;
  commits.value = await (await fetch(url)).json();
  console.warn(commits.value);
});
</script>

<template>
  <h1>Latest Vue Core Commits</h1>
  <!-- radio option -->
  <template v-for="(branch, idx) in branches">
    <input
      type="radio"
      name="branch"
      id="idx"
      :value="branch"
      v-model="currentBranch"
    />
    <label :for="branch"> {{ branch }}</label>
  </template>
  <ul>
    <li v-for="{ author } in commits">
      {{ author }}
    </li>
  </ul>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
