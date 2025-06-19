<template>
  <div class="absolute inset-0">
    <!-- 锁图标遮罩层 -->
    <div class="absolute inset-0 z-3">
      <div class="w-full h-full rounded-box bg-base-100 mask-l-from-25% mask-l-to-75%
      grid grid-cols-4 grid-rows-1">
        <div class="col-start-4 flex items-center justify-center">
          <span class="icon-[tabler--lock-filled] size-10 text-neutral/10"></span>
        </div>
      </div>
    </div>

    <!-- 网格图案遮罩层 -->
    <div class="absolute inset-0 z-2">
      <div class="w-full h-full rounded-box bg-base-100/50
      bg-[image:repeating-linear-gradient(315deg,_var(--pattern-fg)_0,_var(--pattern-fg)_1px,_transparent_0,_transparent_50%)] 
      bg-[size:10px_10px] [--pattern-fg:var(--color-neutral)]/10">
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// 组件可以接收props，如不同的遮罩样式、颜色等
</script> 