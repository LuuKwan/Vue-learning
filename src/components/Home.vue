<script setup>
import { ref, computed } from "vue";

defineProps({
  msg: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <h1>This is Home Page</h1>
  <h2>Publish book --> {{ publishedBooks }}</h2>
  <h3>book list -> {{ author.books }}</h3>
  <button @click="emptyBook('vue1')">Empty book</button>
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
