<template>
    <div class="min-h-screen h-full">
        <v-chart class="chart" :option="option" autoresize />
    </div>
</template>

<script setup>
import { use } from "echarts/core";
import { CanvasRenderer } from "echarts/renderers";
import { PieChart } from "echarts/charts";
import {
  TitleComponent,
  TooltipComponent,
  LegendComponent
} from "echarts/components";
import VChart, { THEME_KEY } from "vue-echarts";
import { ref, provide } from "vue";

use([
  CanvasRenderer,
  PieChart,
  TitleComponent,
  TooltipComponent,
  LegendComponent
]);

const ONE_UNIT_IN_PERCENTS = 1.1764;
// 4.2352 deg - one element, 1.1764 percent one elemnent
const option = ref({
  tooltip: {
    trigger: 'item',
    formatter: '{a}123 <br/>{b}: {c} ({d}%)',
  },
  height: "100%",
  series: [
    {
      name: 'Access From',
      type: 'pie',
      radius: ['15%', '50%'],
      label: {
        position: 'inner',
        fontSize: 12,
      },
      labelLine: {
        show: false
      },
      data: [
        { value: ONE_UNIT_IN_PERCENTS * 4, name: 'Цветочный', itemStyle: { color: '#da0d68' } },
        { value: ONE_UNIT_IN_PERCENTS * 14, name: 'Фруктовый', itemStyle: { color: '#da1d23' } },
        { value: ONE_UNIT_IN_PERCENTS * 10, name: 'Кислый', itemStyle: { color: '#eab40c' } },
        { value: ONE_UNIT_IN_PERCENTS * 10, name: 'Растительный', itemStyle: { color: '#19792f' } },
        { value: ONE_UNIT_IN_PERCENTS * 16, name: 'Другие', itemStyle: { color: '#0aa3b5' } },
        { value: ONE_UNIT_IN_PERCENTS * 8, name: 'Печёный', itemStyle: { color: '#c94930' }},
        { value: ONE_UNIT_IN_PERCENTS * 6, name: 'Пряный', itemStyle: { color: '#ac2140' }},
        { value: ONE_UNIT_IN_PERCENTS * 5, name: 'Ореховый/Какао', itemStyle: { color: '#a67c64' }},
        { value: ONE_UNIT_IN_PERCENTS * 9, name: 'Сладкий', itemStyle: { color: '#e65832' }},
      ]
    },
    {
      name: 'Access From',
      type: 'pie',
      radius: ['50%', '95%'],
      labelLine: {
        show: false
      },
      label: {
        position: "inner",
        formatter: '{b}',
        fontSize: 10,
      },
      data: [
        { value: 0, name: 'Baidu' },
        { value: 0, name: 'Direct' },
        { value: 0, name: 'Email' },
        { value: 0, name: 'Google' },
        { value: 0, name: 'Union Ads' },
        { value: 0, name: 'Bing' },
        { value: 0, name: 'Video Ads' },
        { value: 0, name: 'Others' }
      ]
    }
  ]
});
</script>

<style scoped>
.chart {
  height: 100vh;
}
</style>