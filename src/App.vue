<script setup lang="ts">
import DictionaryCard from "./components/DictionaryCard.vue";
</script>

<template>
  <main>
    <DictionaryCard
      title="Pillepalle"
      pos="/NOUN/"
      definition="A delightfully pointless little thing, far too insignificant to be worth getting upset about."
      example="Roman macht Drama daraus, aber ehrlich gesagt ist es Pillepalle."
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
