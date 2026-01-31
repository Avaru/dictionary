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
  font-family: var(--font-title);
  font-size: clamp(32px, 10vw, 64px);
  line-height: 1;
  color: var(--accent);
  margin: 0 0 8px 0;
}

.type {
  font-family: var(--font-type);
  letter-spacing: 0.04em;
  font-size: clamp(16px, 3vw, 16px);
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
  font-family: var(--font-body);
  width: 100%;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none;
  font-weight: 300;
}

.card-body::-webkit-scrollbar {
  display: none;
}

.definition {
  font-size: clamp(16px, 3.5vw, 20px);
  line-height: 1.8;
  margin: 0 0 16px 0;
}

.example {
  font-size: clamp(15px, 3.2vw, 18px);
  font-style: italic;
  margin: 0;
}

@media (orientation: portrait) and (max-width: 720px) {
  .dictionary-card {
    padding: 20px 18px;
  }
}

@media print {
  .dictionary-card {
    width: 9.5cm;
    height: 9.5cm;
    page-break-inside: avoid;
    margin: 0.5cm;
    padding: 0.5cm;
    border: 1px solid #000;
    justify-content: center;
    align-items: flex-start;
    text-align: left;
    overflow: visible;
    background: #fff;
    aspect-ratio: auto;
  }

  @page {
    margin: 0cm;
  }

  .card-header {
    margin-bottom: 10px;
    width: 100%;
  }

  .title {
    font-size: 30px;
    line-height: 1.1;
    margin: 0 0 3px 0;
  }

  .type {
    font-size: 9px;
    margin-bottom: 5px;
    font-weight: 700;
  }

  .rule {
    margin: 5px 0 7px 0;
  }

  .card-body {
    overflow: visible;
  }

  .definition {
    font-size: 10px;
    line-height: 1.35;
    margin: 0 0 5px 0;
  }

  .example {
    font-size: 9px;
    line-height: 1.35;
  }
}
</style>
