<script setup lang="ts">
import Card from './components/Card.vue';
import { onMounted, nextTick } from 'vue';
import Sortable from 'sortablejs';

onMounted(async () => {
  // 等待下一个DOM更新周期
  await nextTick();
  
  // 初始化Card容器的拖拽功能
  const cardContainer = document.querySelector('#card-container') as HTMLElement;
  if (cardContainer) {
    Sortable.create(cardContainer, {
      animation: 150,
      // 移除handle选项，使整个Card可拖拽
      dragClass: '!border-0',
      ghostClass: 'opacity-70' // 拖动时的半透明效果
    });
  }
  
  // 初始化其他组件
  setTimeout(() => window.HSStaticMethods.autoInit(), 100);
});
</script>

<template>
  <div class="p-2 bg-base-200">
    <div id="card-container" class="flex flex-col gap-1 py-4 w-full md:w-2xl md:mx-auto">
      <div v-for="(_, index) in 6" :key="index" class="relative group cursor-move">
        <!-- 移除拖拽把手，整个卡片可拖拽 -->
        <Card />
      </div>
    </div>
  </div>
</template>