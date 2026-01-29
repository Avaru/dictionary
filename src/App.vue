<script setup lang="ts">
import { computed } from "vue";
import DictionaryCard from "./components/DictionaryCard.vue";
import dictionary from "./dictionary";
const currentWord = computed(
  () =>
    dictionary[0] as {
      word: string;
      type: string;
      definition: string;
      example: string;
    },
);
</script>

<template>
  <main>
    <DictionaryCard v-bind="currentWord" />
  </main>
</template>

<style scoped>
main {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}
</style>
