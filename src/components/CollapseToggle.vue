<template>
  <label class="swap cursor-pointer">
    <input type="checkbox" :checked="modelValue" @change="onChange" />
    <div class="swap-on flex items-center gap-2">
      <span class="icon-[tabler--layout-bottombar-expand-filled] size-7"></span>
    </div>
    <div class="swap-off flex items-center gap-2">
      <span class="icon-[tabler--layout-bottombar-collapse] size-7"></span>
    </div>
  </label>
</template>

<script setup lang="ts">
defineProps<{
  modelValue: boolean;
}>();

const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void;
}>();

const onChange = (event: Event) => {
  const target = event.target as HTMLInputElement;
  emit('update:modelValue', target.checked);
};
</script> 