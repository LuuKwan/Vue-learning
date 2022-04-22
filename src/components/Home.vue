<script setup>
import { ref, computed } from "vue";

import SlotComp from "./SlotComp.vue";

defineProps({
  msg: {
    type: String,
    required: true,
  },
});
const books = ref(["naruto", "dragon ball"]);
</script>

<template>
  <h1>This is Home Page</h1>
  <!-- Passing Parent's state into slot child -->
  <SlotComp #bottom>
    <p v-for="book in books">{{ book }}</p>
  </SlotComp>
  <br />
  <!-- using parent prop to access slot state -->
  <SlotComp #top="{ source }"></SlotComp>
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
