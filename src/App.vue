<script setup lang="ts">
import { onMounted, ref } from 'vue';
import CardContainer from './components/CardContainer.vue';
import ProgressStep from './components/ProgressStep.vue';
import Navbar from './components/Navbar.vue';
import ToggleCount from './components/ToggleCount.vue'
import StatusBar from './components/StatusBar.vue';

const showAllDetails = ref(true);

onMounted(() => {
  // 初始化其他组件
  setTimeout(() => window.HSStaticMethods.autoInit(), 100);
});
</script>

<template>
  <Navbar v-model="showAllDetails" />

  <div class="p-2 flex flex-col gap-2">
    <ProgressStep :current-step="10" :total-steps="20" :is-completed="false" />
    <div class="grid grid-cols-2">
      <ToggleCount />
      <StatusBar />
    </div>

    <CardContainer :show-details="showAllDetails" />
  </div>
</template>