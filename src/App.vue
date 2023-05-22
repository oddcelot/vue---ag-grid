<script setup lang="ts">
import Grid from './components/Grid.vue';
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
    <br />
    <a href="https://ag-grid.com/" target="_blank">
      <img src="https://blog.ag-grid.com/content/images/2021/02/logo-white.svg" class="logo ag-grid" alt="Vue logo" />
    </a>
  </div>
  <Grid />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
.logo.ag-grid:hover {
  filter: drop-shadow(0 0 2em #007bff);
}
</style>
