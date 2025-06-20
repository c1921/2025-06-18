<template>
  <div id="card-container" class="flex flex-col gap-1 w-full md:w-2xl md:mx-auto">
    <!-- 前三个卡片（已解锁） -->
    <div v-for="index in 3" :key="'unlocked-'+index" class="relative group cursor-move">
      <Card :locked="false" :show-details="showDetails" />
    </div>

    <!-- 后三个卡片（未解锁） -->
    <div v-for="index in 3" :key="'locked-'+index" class="relative group cursor-move">
      <Card :locked="true" :show-details="showDetails" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, nextTick } from 'vue';
import Sortable from 'sortablejs';
import Card from './Card.vue';

// 定义props
defineProps<{
  showDetails: boolean;
}>();

onMounted(async () => {
  // 等待下一个DOM更新周期
  await nextTick();
  
  // 初始化Card容器的拖拽功能
  const cardContainer = document.querySelector('#card-container') as HTMLElement;
  if (cardContainer) {
    Sortable.create(cardContainer, {
      animation: 150,
      dragClass: '!border-0',
      ghostClass: 'opacity-70' // 拖动时的半透明效果
    });
  }
});
</script> 