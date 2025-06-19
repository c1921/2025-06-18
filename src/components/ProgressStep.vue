<template>
  <div class="flex items-center gap-x-1">
    <div 
      v-for="step in totalSteps" 
      :key="step"
      class="progress-step" 
      :class="step <= currentStep ? 'bg-primary' : 'bg-primary/10'"
      role="progressbar" 
      aria-label="Progressbar" 
      :aria-valuenow="step <= currentStep ? 100 : 0"
      aria-valuemin="0" 
      aria-valuemax="100"
    ></div>
    <p class="size-6">
      <span 
        :class="[
          'icon-[tabler--circle-check-filled] size-6', 
          isCompleted ? 'text-primary' : 'text-primary/10'
        ]"
      ></span>
    </p>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

interface Props {
  currentStep: number;
  totalSteps: number;
  isCompleted?: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  currentStep: 0,
  totalSteps: 10,
  isCompleted: false
});
</script>