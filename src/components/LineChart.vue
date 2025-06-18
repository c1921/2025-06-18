<template>
  <div class="chart-container">
    <canvas ref="chartCanvas"></canvas>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, watch, defineProps, withDefaults } from 'vue';
import { Chart, registerables } from 'chart.js';
import type { ChartData, ChartOptions } from 'chart.js';

// 注册所有Chart.js组件
Chart.register(...registerables);

interface Props {
  chartData: {
    labels: string[];
    datasets: {
      label: string;
      data: number[];
      borderColor?: string;
      backgroundColor?: string;
      tension?: number;
      fill?: boolean;
    }[];
  };
  options?: ChartOptions;
}

const props = withDefaults(defineProps<Props>(), {
  options: () => ({})
});

const chartCanvas = ref<HTMLCanvasElement | null>(null);
let chart: Chart | null = null;

onMounted(() => {
  if (chartCanvas.value) {
    createChart();
  }
});

// 监听数据变化，更新图表
watch(() => props.chartData, (newData) => {
  if (chart) {
    chart.data = newData as ChartData;
    chart.update();
  }
}, { deep: true });

// 创建图表
const createChart = () => {
  if (!chartCanvas.value) return;
  
  const ctx = chartCanvas.value.getContext('2d');
  if (!ctx) return;
  
  // 销毁旧图表（如果存在）
  if (chart) {
    chart.destroy();
  }
  
  // 创建新图表
  chart = new Chart(ctx, {
    type: 'line',
    data: props.chartData as ChartData,
    options: {
      responsive: true,
      maintainAspectRatio: false,
      ...props.options
    }
  });
};
</script>