<template>
  <HomePage />
</template>

<script setup>
import HomePage from './components/game/HomePage.vue'
</script>

<style>
body, html, #app {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}

.flex-column {
  display: flex;
  flex-direction: column;
}

.flex-row {
  display: flex;
  flex-direction: row;
}

.gap-10 { gap: 10px; }

.flex-center {
  align-items: center;
  justify-content: center;
}
</style>
