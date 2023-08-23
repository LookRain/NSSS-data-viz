<template>
  <v-chart class="chart" :option="option" autoresize />
</template>

<script setup>
import VChart, { THEME_KEY } from "vue-echarts";
import "echarts";

const option = ref({
  backgroundColor: "white",
  title: {
    //text: "Customized Pie",
    left: "center",
    top: 20,
    textStyle: {
      color: "#383838",
    },
  },
  // tooltip: {
  //   trigger: 'item',
  // },
  visualMap: {
    show: true,
    min: 1,
    max: 50,
    inRange: {
      colorLightness: [0.9, 0.01],
    },
  },
  series: [
    {
      name: "Access From",
      type: "pie",
      radius: "55%",
      center: ["50%", "50%"],
      data: [
        { value: 27.3, name: "STUDENT RESIDENCES" },
        { value: 26.7, name: "Clubs & societies, events & spaces" },
        { value: 20.7, name: "At a private home/residence" },
        { value: 17.9, name: "General campus areas" },
        { value: 16.6, name: "Hospitality/retail areas off campus" },
        { value: 10.4, name: "Hospitality/retail areas on campus" },
        { value: 7.0, name: "University library" },
        { value: 6.0, name: "University lecture theatres/computer labs" },
        { value: 4.0, name: "On work experience/professional placement" },
        { value: 3.0, name: "Sports & recreational areas on campus" },
        { value: 2.6, name: "Somewhere else" },
        { value: 1.7, name: "Academic/administrative staff office" },
      ].sort(function (a, b) {
        return a.value - b.value;
      }),
      roseType: "radius",
      label: {
        fontSize: 12,
        fontWeight: "300",
        color: "#383838",
        formatter: function (params) {
          // Check if it's the special data point
          if (params.name === "STUDENT RESIDENCES") {
            return `{a|${params.name}}`; // The name is already formatted with rich text
          } else {
            return params.name;
          }
        },
        rich: {
          a: {
            fontSize: 32, // This will be the bigger font size for the special data point
            color: "#3d0a02",
            fontWeight: "500",
          },
          b: {},
        },
      },
      labelLine: {
        lineStyle: {
          color: "#c9c9c9",
        },
        smooth: 0.2,
        length: 10,
        length2: 20,
      },
      itemStyle: {
        color: "#c23531",
        shadowBlur: 100,
        shadowColor: "rgba(0, 0, 0, 0.5)",
      },
      animationType: "scale",
      animationEasing: "elasticOut",
      animationDelay: function (idx) {
        return idx * 150;
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
