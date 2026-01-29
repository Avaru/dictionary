<template>
  <article class="dictionary-card">
    <header class="card-header">
      <h1 class="title">{{ word }}</h1>
      <div class="type">{{ type }}</div>
      <hr class="rule" />
    </header>

    <section class="card-body">
      <p class="definition">{{ definition }}</p>
      <p class="example">{{ example }}</p>
    </section>
  </article>

  <ButtonGroup @next="$emit('next')" @prev="$emit('prev')" @random="$emit('random')" />
</template>

<script setup lang="ts">
import ButtonGroup from "./ButtonGroup.vue";

defineProps<{
  word: string;
  type: string;
  definition: string;
  example: string;
}>();

defineEmits<{
  prev: [];
  next: [];
  random: [];
}>();
</script>

<style scoped>
:root {
  --card-width: 700px;
  --card-bg: #fbfbfb;
  --card-border: #222;
  --accent: #000;
  --footer-height: 72px;
  --title-font: "Playfair Display", serif;
  --body-font: "Poppins", "Helvetica Neue", Arial, sans-serif;
}

.dictionary-card {
  box-sizing: border-box;
  width: 100%;
  max-width: min(92vw, 480px);
  margin: 24px auto;
  padding: 28px 22px;
  background: #fff;
  border: none;
  box-shadow: none;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  text-align: center;
  overflow: hidden;
}

.card-header {
  margin-bottom: 18px;
  width: 100%;
}

.title {
  font-family: var(--title-font);
  font-size: clamp(48px, 12vw, 80px);
  line-height: 1;
  color: var(--accent);
  margin: 0 0 8px 0;
  font-weight: 400;
}

.type {
  font-family: var(--body-font);
  font-weight: 700;
  letter-spacing: 0.04em;
  font-size: clamp(11px, 2.5vw, 14px);
  color: var(--accent);
  margin-bottom: 8px;
  font-variant: small-caps;
}

.rule {
  border: none;
  border-top: 1px solid #000;
  margin: 12px 0 18px 0;
}

.card-body {
  font-family: var(--body-font);
  width: 100%;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none;
}

.card-body::-webkit-scrollbar {
  display: none;
}

.definition {
  font-size: clamp(14px, 3vw, 20px);
  line-height: 1.8;
  margin: 0 0 16px 0;
}

.example {
  font-size: clamp(13px, 2.8vw, 18px);
  font-style: italic;
  margin: 0;
}

@media (orientation: portrait) and (max-width: 720px) {
  .dictionary-card {
    padding: 20px 18px;
  }
}

@media (min-width: 720px) {
  .dictionary-card {
    width: var(--card-width);
    max-width: 90vw;
    aspect-ratio: 1 / 1;
    padding: 56px 64px;
    margin: 48px auto;
    justify-content: center;
    border: 1px solid #000;
    box-shadow: none;
    align-items: flex-start;
    text-align: left;
  }

  .card-header {
    margin-bottom: 28px;
  }

  .title {
    font-size: 64px;
  }

  .type {
    font-size: 14px;
    margin-bottom: 12px;
  }

  .rule {
    margin: 16px 0 24px 0;
  }

  .definition {
    font-size: 20px;
    margin: 0 0 20px 0;
  }

  .example {
    font-size: 18px;
  }
}
</style>
