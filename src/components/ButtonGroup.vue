<template>
  <div :class="['button-group', position]">
    <button type="button">Prev</button>
    <button type="button">Next</button>
    <button type="button">Random</button>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  position?: "fixed" | "static";
}>();
</script>

<style scoped>
.button-group {
  display: flex;
  gap: 12px;
  width: 100%;
  max-width: 520px;
  justify-content: center;
}

.button-group.fixed {
  position: fixed;
  left: 0;
  right: 0;
  bottom: env(safe-area-inset-bottom, 0);
  height: var(--footer-height, 72px);
  margin: 0;
  align-items: center;
  background: transparent;
  z-index: 40;
  width: 100%;
  max-width: 100%;
}

.button-group.static {
  display: none; /* hidden on mobile, shown on desktop */
  margin-top: 28px;
  justify-content: flex-start;
}

button {
  appearance: none;
  -webkit-appearance: none;
  border: 1px solid #000;
  background: #fff;
  padding: 10px 14px;
  border-radius: 8px;
  font-family: inherit;
  font-weight: 600;
  cursor: pointer;
  flex: 1 1 0;
  max-width: 160px;
  color: #000;
}

button:hover {
  background: #000;
  color: #fff;
}

@media (min-width: 720px) {
  .button-group {
    max-width: none;
    justify-content: flex-start;
  }

  .button-group.fixed {
    display: none; /* hide fixed buttons on desktop */
  }

  .button-group.static {
    display: flex; /* show static buttons on desktop */
    margin-top: 28px;
  }

  button {
    flex: 0 0 auto;
    min-width: 110px;
  }
}
</style>
