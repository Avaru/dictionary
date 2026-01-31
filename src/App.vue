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
  <main class="screen-view">
    <DictionaryCard
      v-bind="currentWord"
      @next="nextWord()"
      @prev="prevWord()"
      @random="randomWord()"
    />
  </main>

  <main class="print-view">
    <DictionaryCard v-for="word in dictionary" :key="word.word" v-bind="word" />
  </main>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=League+Spartan:wght@100..900&family=Playfair+Display:ital,wght@0,400..900;1,400..900&family=Roboto:ital,wght@0,100..900;1,100..900&display=swap");
main {
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.screen-view {
  min-height: 100vh;
}

.print-view {
  display: none;
}

@media print {
  .screen-view {
    display: none;
  }

  .print-view {
    display: grid;
    grid-template-columns: 1fr 1fr;
    min-height: auto;
    overflow: visible;
    width: 100%;
    padding: 0.5cm;
    gap: 0;
  }
}

:root {
  --font-title: "Playfair Display", serif;
  --font-body: "Roboto", "Helvetica Neue", Arial, sans-serif;
  --font-type: "League Spartan", sans-serif;
}
</style>
