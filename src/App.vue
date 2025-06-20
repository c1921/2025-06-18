<script setup lang="ts">
import { onMounted, ref } from 'vue';
import CardContainer from './components/CardContainer.vue';
import ProgressStep from './components/ProgressStep.vue';
import Navbar from './components/Navbar.vue';

const showAllDetails = ref(true);

onMounted(() => {
  // 初始化其他组件
  setTimeout(() => window.HSStaticMethods.autoInit(), 100);
});
</script>

<template>
  <Navbar v-model="showAllDetails" />
  
  <div class="p-2 bg-base-200">
    <ProgressStep :current-step="10" :total-steps="20" :is-completed="false" />

    <CardContainer :show-details="showAllDetails" />
  </div>
</template>