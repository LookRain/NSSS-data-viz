<template>
  <v-chart class="chart" :option="option" autoresize />
</template>

<script setup>
import VChart, { THEME_KEY } from "vue-echarts";
import "echarts";

const dataSet = [
  [
    {
      value: 51,
      name: "know nothing/very little ", //about formal harassment reporting processes",
    },
    {
      value: 49,
      name: "know something or more",
      label: {
        show: false,
      },
    },
  ],
  [
    {
      value: 53.6,
      name: "know nothing/very little", //about formal assault reporting processes",
    },
    {
      value: 46.4,
      name: "know something or more",
      label: {
        show: false,
      },
    },
  ],
  [
    {
      value: 46.7,
      name: "know nothing or very little", // about where to seek support or assistance for harassment",
    },
    {
      value: 53.3,
      name: "know something or more",
      label: {
        show: false,
      },
    },
  ],
  [
    {
      value: 43.5,
      name: "know nothing/very little", // about where to seek support for assault",
    },
    {
      value: 56.5,
      name: "know something or more",
      label: {
        show: false,
      },
    },
  ],
];

const index = ref(0);

const option = ref({
  tooltip: {
    trigger: "item",
  },
  legend: {
    top: "5%",
    left: "center",
    // data: [
    //   "Know nothing/very little about formal harassment reporting processes",
    //   "Know nothing/very little about formal assault reporting processes",
    //   "Know nothing/very little about where to seek support for harassment",
    //   "Know nothing/very little about where to seek support for assault",
    // ],
  },
  series: [
    {
      name: "Access From",
      type: "pie",
      radius: ["40%", "70%"],
      center: ["30%", "50%"],
      avoidLabelOverlap: false,
      itemStyle: {
        borderRadius: 10,
        borderColor: "#fff",
        borderWidth: 2,
      },
      label: {
        textStyle: {
          fontSize: 26,
        },
        show: true,
        formatter: "{c}% " + "{b}",
      },
      emphasis: {
        label: {
          show: false,
          fontSize: 40,
          fontWeight: "bold",
        },
      },
      labelLine: {
        show: true,
      },
      data: dataSet[index.value],
    },
  ],
  color: ["#c23531", "black"],
});

onMounted(() => {
  setInterval(() => {
    // cycle index from 0 - 3
    index.value = (index.value + 1) % 4;
    option.value.series[0].data = dataSet[index.value];
  }, 5000);
});
</script>
<style scoped>
.chart {
  height: 100vh;
}
</style>
