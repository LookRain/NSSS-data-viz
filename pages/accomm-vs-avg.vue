<template>
  <v-chart class="chart" :option="option" autoresize />
</template>

<script setup>
import VChart, { THEME_KEY } from "vue-echarts";
import "echarts";

const rawData = [4.5, 8.8].sort();
// const colors = [
//   '#c23531',
//   '#ae2f2c',
//   '#9b2a27',
//   '#872522',
//   '#741f1d',
//   '#611a18',
//   '#4d1513',
//   '#3a0f0e',
//   '#260a09',
//   '#130504',
//   '#000000',
// ];

const option = ref({
  xAxis: {
    type: "category",
    data: ["Average", "Student Residences"],
    axisLabel: {
      fontSize: 25,
      // inside: true,
      color: "black",
    },
  },
  yAxis: {
    type: "value",
    fontSize: 50,
    color: "#999",
    name: "%",
  },
  backgroundColor: "white",
  visualMap: {
    show: false,
    min: 1,
    max: 100,
    inRange: {
      colorLightness: [0.8, 0.1],
    },
  },
  series: [
    {
      data: rawData,
      type: "bar",
      // showBackground: true,
      color: "#c23531",
      label: {
        show: true, // This line makes the label visible
        formatter: "{c}%",
        position: "top", // This line sets the position of the label
        color: "black", // This line sets the color of the label text
        fontSize: 36,
      },
      animationDelay: function (idx) {
        return idx * 1000;
      },
    },
  ],
});
</script>
<style scoped>
.chart {
  height: 100vh;
}
</style>
