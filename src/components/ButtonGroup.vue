<template>
  <div class="button-group fixed">
    <button @click="$emit('prev')">Prev</button>
    <button @click="$emit('random')">Random</button>
    <button @click="$emit('next')">Next</button>
  </div>
  <div class="button-group static">
    <button @click="$emit('prev')">Prev</button>
    <button @click="$emit('random')">Random</button>
    <button @click="$emit('next')">Next</button>
  </div>
</template>

<script setup lang="ts">
defineEmits<{
  prev: [];
  next: [];
  random: [];
}>();
</script>

<style scoped>
.button-group {
  display: flex;
  gap: 12px;
  width: 100vw;
  justify-content: center;
}

.button-group.fixed {
  position: fixed;
  left: 0;
  right: 0;
  bottom: env(safe-area-inset-bottom, 0);
  align-items: stretch;
  z-index: 40;
  width: 100%;
  padding: 2rem;
  box-sizing: border-box;
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
  padding: 0.5rem 1rem;
  border-radius: 8px;
  font-family: inherit;
  font-weight: 600;
  cursor: pointer;
  flex-grow: 1;
  color: #000;
  user-select: none;
  -webkit-user-select: none;
  -webkit-touch-callout: none;
  touch-action: manipulation;
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
