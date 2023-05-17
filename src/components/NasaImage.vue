<script setup lang="ts">
import { useFetch } from '@vueuse/core';
import { computed } from 'vue';

interface ImageInfo {
  url: string;
  explanation: string;
  title: string;
  copyright?: string;
}

const { isFetching, error, data } = await useFetch<string>(
  'https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY'
);
const imageData = computed<ImageInfo>(() => (data.value ? JSON.parse(data.value) : { url: '' }));
console.log(imageData.value);
</script>

<template>
  <p v-if="error">{{ error }}</p>
  <section v-if="data">
    <span v-if="imageData.copyright">Image &copy; {{ imageData.copyright }}</span>
    <p>{{ imageData.explanation }}</p>
    <img :src="imageData.url" :alt="imageData.title" />
  </section>
</template>
