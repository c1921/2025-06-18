<script setup lang="ts">
import Card from './components/Card.vue';
import { onMounted } from 'vue';

onMounted(() => {
  setTimeout(() => window.HSStaticMethods.autoInit(), 100)
});
</script>

<template>
  <div class="p-2 bg-base-200">
    <div class="flex flex-col gap-1 py-4 w-full md:w-2xl md:mx-auto">
      <Card />
      <Card />
      <Card />
    </div>
  </div>
</template>