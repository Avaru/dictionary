<script setup lang="ts">
import { computed, onMounted, ref } from "vue";
import DictionaryCard from "./components/DictionaryCard.vue";
import dictionary from "./dictionary";

const currentIndex = ref(0);
const currentWord = computed(
  () =>
    dictionary[currentIndex.value] as {
      word: string;
      type: string;
      definition: string;
      example: string;
    },
);

const nextWord = () => {
  currentIndex.value = (currentIndex.value + 1) % dictionary.length;
};

const prevWord = () => {
  currentIndex.value = (currentIndex.value - 1 + dictionary.length) % dictionary.length;
};

const randomWord = () => {
  currentIndex.value = Math.floor(Math.random() * dictionary.length);
};

onMounted(() => {
  randomWord();
});
</script>

<template>
  <main>
    <DictionaryCard
      v-bind="currentWord"
      @next="nextWord()"
      @prev="prevWord()"
      @random="randomWord()"
    />
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
