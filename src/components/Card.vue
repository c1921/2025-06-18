<template>
  <div class="relative rounded-box p-2.5 bg-base-100 group hover:bg-base-100/50 transition duration-500">
    <div class="relative flex gap-3 z-10">

      <div class="progress progress-vertical h-auto" role="progressbar" aria-valuenow="25" aria-valuemin="0"
        aria-valuemax="100">
        <div class="progress-bar h-1/4"></div>
      </div>

      <div class="flex-1">

        <div class="flex items-center justify-between">
          <div class="flex items-center gap-2">
            <div class="inline-grid *:[grid-area:1/1]">
              <div class="status status-error animate-ping"></div>
              <div class="status status-error"></div>
            </div>
            <span class="icon-[tabler--sword]"></span>
            <span class="font-bold">Server</span>
          </div>
          <div class="flex gap-1">
            <p class="text-base-content/90 font-medium">24,895</p>
            <p class="text-success/80 flex items-center text-xs">
              <span class="icon-[tabler--chevrons-up] size-3.5 me-0.5"></span>
              10%
            </p>
          </div>
        </div>

        <div class="flex justify-between items-end">
          <div class="grid grid-cols-3">
            <span class="icon-[tabler--alert-triangle] size-5 text-warning/50"></span>
            <span class="icon-[tabler--alert-triangle] size-5 text-warning/50"></span>
            <span class="icon-[tabler--alert-triangle] size-5 text-warning/50"></span>



          </div>

          <div class="flex-1 w-32 h-10 mask-radial-[100%_100%] mask-radial-from-70% mask-radial-at-right">
            <canvas ref="chartCanvas"></canvas>
          </div>

        </div>

      </div>

    </div>
    <div class="absolute inset-0 z-0">
      <!-- 背景内容-->
      <div class="w-full h-full rounded-box
        bg-linear-to-b from-primary/30 group-hover:from-primary to-30%
        mask-x-from-65% mask-x-to-100%
        animate-pulse group-hover:animate-none transition duration-500">
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import { Chart, registerables } from 'chart.js';
import type { ChartData, ScriptableContext } from 'chart.js';

// 注册所有Chart.js组件
Chart.register(...registerables);

const chartCanvas = ref<HTMLCanvasElement | null>(null);
let chart: Chart | null = null;
let updateInterval: number | null = null;

const MAX_DATA_POINTS = 50;

// 初始数据
const initialData = Array(MAX_DATA_POINTS).fill(0).map(() => Math.floor(Math.random() * 50) + 30);

// 图表数据
const chartData = {
  labels: Array(MAX_DATA_POINTS).fill(''),
  datasets: [
    {
      label: '趋势',
      data: initialData,
      borderColor: '#36A2EB',
      backgroundColor: function(context: ScriptableContext<'line'>) {
        const chart = context.chart;
        const {ctx, chartArea} = chart;
        
        if (!chartArea) {
          // 如果图表区域未定义，返回默认颜色
          return 'rgba(54, 162, 235, 0.1)';
        }
        
        // 创建渐变
        const gradient = ctx.createLinearGradient(0, chartArea.bottom, 0, chartArea.top);
        gradient.addColorStop(0, 'rgba(54, 162, 235, 0)');     // 底部完全透明
        gradient.addColorStop(0.5, 'rgba(54, 162, 235, 0.1)'); // 中部轻微透明
        gradient.addColorStop(1, 'rgba(54, 162, 235, 0.25)');  // 顶部更不透明
        
        return gradient;
      },
      tension: 0.4,
      fill: true,
      borderWidth: 1.5
    }
  ]
};

// 图表配置
const chartOptions = {
  plugins: {
    tooltip: {
      enabled: false
    },
    legend: {
      display: false
    }
  },
  scales: {
    x: {
      display: false
    },
    y: {
      display: false,
      beginAtZero: true
    }
  },
  responsive: true,
  maintainAspectRatio: false,
  elements: {
    point: {
      radius: 0
    },
    line: {
      borderJoinStyle: 'round' as const
    }
  },
  animations: {
    y: {
      duration: 0 // 将Y轴动画禁用
    }
  }
};

onMounted(() => {
  if (chartCanvas.value) {
    createChart();
    startDataUpdates();
  }
});

onUnmounted(() => {
  stopDataUpdates();
});

// 创建图表
const createChart = () => {
  if (!chartCanvas.value) return;
  
  const ctx = chartCanvas.value.getContext('2d');
  if (!ctx) return;
  
  // 创建图表
  chart = new Chart(ctx, {
    type: 'line',
    data: chartData as ChartData,
    options: chartOptions
  });
};

// 开始数据更新
const startDataUpdates = () => {
  updateInterval = window.setInterval(() => {
    if (chart) {
      // 生成新的随机数据点
      const newValue = Math.floor(Math.random() * 50) + 30;
      
      // 移除第一个数据点并添加新数据点到末尾
      const data = chart.data.datasets[0].data;
      data.shift();
      data.push(newValue);
      
      // 更新图表
      chart.update();
    }
  }, 1000);
};

// 停止数据更新
const stopDataUpdates = () => {
  if (updateInterval !== null) {
    clearInterval(updateInterval);
    updateInterval = null;
  }
};
</script>
