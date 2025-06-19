<script setup lang="ts">
import { onMounted } from 'vue';
import CardContainer from './components/CardContainer.vue';
import ProgressStep from './components/ProgressStep.vue';
import ThemeController from './components/ThemeController.vue';
import StatusBar from './components/StatusBar.vue';

onMounted(() => {
  // 初始化其他组件
  setTimeout(() => window.HSStaticMethods.autoInit(), 100);
});
</script>

<template>
  <div class="p-2 bg-base-200">

    <ThemeController />
    <ProgressStep :current-step="10" :total-steps="20" :is-completed="false" />
    <StatusBar />
    <CardContainer />
    
  </div>
</template>