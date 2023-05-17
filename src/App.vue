<script setup lang="ts">
import NasaImage from './components/NasaImage.vue'
</script>

<template>
  <header>
    <p>Header</p>
  </header>

  <main>
    <h1>App</h1>
    <Suspense>
      <NasaImage />
      <template #fallback> Loading... </template>
    </Suspense>
  </main>
</template>
