<template>
  <article class="dictionary-card">
    <header class="card-header">
      <h1 class="title">{{ title }}</h1>
      <div class="pos">{{ pos }}</div>
      <hr class="rule" />
    </header>

    <section class="card-body">
      <p class="definition">{{ definition }}</p>
      <p class="example">{{ example }}</p>
    </section>
    <footer class="card-footer">
      <div class="controls">
        <button>Prev</button>
        <button>Next</button>
        <button>Random</button>
      </div>
    </footer>
  </article>

  <div class="external-controls">
    <button>Prev</button>
    <button>Next</button>
    <button>Random</button>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  title: string;
  pos: string;
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
  font-size: clamp(48px, 14vw, 96px);
  line-height: 1;
  color: var(--accent);
  margin: 0 0 8px 0;
  font-weight: 400;
}

.pos {
  font-family: var(--body-font);
  font-weight: 700;
  letter-spacing: 0.04em;
  font-size: 13px;
  color: var(--accent);
  margin-bottom: 8px;
}

.rule {
  border: none;
  border-top: 1px solid #000;
  margin: 12px 0 18px 0;
}

.card-body {
  font-family: var(--body-font);
  width: 100%;
}

.definition {
  font-size: 16px;
  line-height: 1.8;
  margin: 0 0 16px 0;
}

.example {
  font-size: 16px;
  font-style: italic;
  margin: 0;
}

@media (orientation: portrait) and (max-width: 720px) {
  .dictionary-card {
    padding: 20px 18px;
  }
  .title {
    font-size: clamp(40px, 16vw, 84px);
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

  .pos {
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

.card-footer {
  width: 100%;
  position: fixed;
  left: 0;
  right: 0;
  bottom: env(safe-area-inset-bottom, 0);
  height: var(--footer-height, 72px);
  margin: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: transparent;
  z-index: 40;
}

.controls {
  display: flex;
  gap: 12px;
  width: 100%;
  max-width: 520px;
  justify-content: center;
}

.card-footer .controls button,
.external-controls button {
  appearance: none;
  -webkit-appearance: none;
  border: 1px solid #000;
  padding: 10px 14px;
  border-radius: 8px;
  font-family: var(--body-font);
  font-weight: 600;
  cursor: pointer;
  flex: 1 1 0;
  max-width: 160px;
  color: #000;
}

.card-footer .controls button:hover,
.external-controls button:hover {
  background: #000;
}

@media (min-width: 720px) {
  .card-footer {
    /* desktop: internal footer is hidden (external controls used) */
    position: static;
    justify-content: flex-start;
    margin-top: 28px;
  }
  .controls {
    justify-content: flex-start;
    max-width: none;
  }
  .card-footer .controls button,
  .external-controls button {
    flex: 0 0 auto;
    min-width: 110px;
  }
}

/* external controls styling: hidden on mobile, visible on desktop outside the card */
.external-controls {
  display: none;
}

@media (min-width: 720px) {
  .external-controls {
    display: flex;
    gap: 12px;
    width: var(--card-width);
    max-width: 90vw;
    margin: 12px auto 0;
    justify-content: flex-start;
  }
  .external-controls button {
    flex: 0 0 auto;
    min-width: 110px;
  }
  /* hide internal footer on desktop (we show external controls instead) */
  .card-footer {
    display: none;
  }
}
</style>
