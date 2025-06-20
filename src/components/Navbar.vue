<template>
  <header class="sticky top-0 z-50 flex min-h-10 px-4 items-center justify-between 
  bg-base-100/60 backdrop-blur-[8px]">
    <ThemeController />
    <CollapseToggle :model-value="modelValue" @update:model-value="onUpdate" />
  </header>
</template>

<script setup lang="ts">
import ThemeController from './ThemeController.vue';
import CollapseToggle from './CollapseToggle.vue';

defineProps<{
  modelValue: boolean;
}>();

const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void;
}>();

const onUpdate = (value: boolean) => {
  emit('update:modelValue', value);
};
</script>