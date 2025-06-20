<template>
  <div class="flex items-center gap-x-1">
    <div 
      v-for="step in totalSteps" 
      :key="step"
      class="progress-step" 
      :class="step <= currentStep ? 'bg-primary/50' : 'bg-primary/10'"
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
          isCompleted ? 'text-primary/50' : 'text-primary/10'
        ]"
      ></span>
    </p>
  </div>
</template>

<script setup lang="ts">

interface Props {
  currentStep: number;
  totalSteps: number;
  isCompleted?: boolean;
}

defineProps<Props>();
</script>
