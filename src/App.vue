<script setup lang="ts">
import { onMounted } from 'vue';
import CardContainer from './components/CardContainer.vue';
import ProgressStep from './components/ProgressStep.vue';

onMounted(() => {
  // 初始化其他组件
  setTimeout(() => window.HSStaticMethods.autoInit(), 100);
});
</script>

<template>
  <div class="p-2 bg-base-200">
    <label class="swap swap-rotate">
      <input type="checkbox" value="light" class="theme-controller" />
      <span class="swap-off icon-[tabler--sun] size-7"></span>
      <span class="swap-on icon-[tabler--moon] size-7"></span>
    </label>
    <ProgressStep :current-step="10" :total-steps="20" :is-completed="false" />
    <CardContainer />
  </div>
</template>