<script setup>
import { ref } from "vue";
const slotAuthor = ref(["Dota", "LOL"]);
</script>

<template>
  <slot name="top" v-bind:source="slotAuthor">
    <h2 v-for="author in slotAuthor">{{ author }}</h2></slot
  >
  <slot name="bottom"> bottom Fallback content</slot>
</template>
