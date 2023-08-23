<template>
  <v-chart class="chart" :option="option" autoresize />
</template>

<script setup>
import VChart, {THEME_KEY} from 'vue-echarts';
import 'echarts';

const dataSet = [
  [
    {
      value: 51,
      name: 'Know nothing or very little about formal reporting processes for harassment',
    },
    {
      value: 49,
      name: 'Know something about formal reporting processes for harassment',
    },
  ],
  [
    {
      value: 53.6,
      name: 'Know nothing or very little about formal reporting processes for assault',
    },
    {
      value: 46.4,
      name: 'Know something about formal reporting processes for assault',
    },
  ],
  [
    {
      value: 46.7,
      name: 'Know nothing or very little about where to seek support or assistance for harassment',
    },
    {
      value: 53.3,
      name: 'Know something about where to seek support or assistance for harassment',
    },
  ],
  [
    {
      value: 43.5,
      name: 'Know nothing or very little about where to seek support or assistance for assault',
    },
    {
      value: 56.5,
      name: 'Know something about where to seek support or assistance for assault',
    },
  ],
];

const index = ref(0);

const option = ref({
  tooltip: {
    trigger: 'item',
  },
  legend: {
    top: '5%',
    left: 'center',
  },
  series: [
    {
      name: 'Access From',
      type: 'pie',
      radius: ['40%', '70%'],
      avoidLabelOverlap: false,
      itemStyle: {
        borderRadius: 10,
        borderColor: '#fff',
        borderWidth: 2,
      },
      label: {
        show: false,
        position: 'center',
      },
      emphasis: {
        label: {
          show: true,
          fontSize: 40,
          fontWeight: 'bold',
        },
      },
      labelLine: {
        show: false,
      },
      data: dataSet[index.value],
    },
  ],
});

onMounted(() => {
  setInterval(() => {
    // cycle index from 0 - 3
    index.value = (index.value + 1) % 4;
    option.value.series[0].data = dataSet[index.value];
  }, 3000);
});
</script>
<style scoped>
.chart {
  height: 100vh;
}
</style>
