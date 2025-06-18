<script setup lang="ts">
import CardContainer from './components/CardContainer.vue';
import { onMounted } from 'vue';

onMounted(() => {
  // 初始化其他组件
  setTimeout(() => window.HSStaticMethods.autoInit(), 100);
});
</script>

<template>
  <div class="p-2 bg-base-200">
    <CardContainer />
  </div>
</template>