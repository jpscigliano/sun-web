<template>
  <component
    :is="chartType"
    :chart-options="chartOptions"
    :chart-data="chartData"
    :chart-id="chartId"
    :dataset-id-key="datasetIdKey"
    :plugins="plugins"
    :css-classes="cssClasses"
    :styles="styles"
    :width="width"
    :height="height"
  />
</template>

<script>
import { Doughnut, Bar, Line } from "vue-chartjs";

export default defineComponent({
  name: "Canvas",
  props: {
    chartOptions: {
      type: Object,
    },
    chartData: {
      type: Object,
    },
    datasetIdKey: {
      type: String,
    },
    chartId: {
      type: String,
      default: "",
    },
    width: {
      type: Number,
      default: 400,
    },
    height: {
      type: Number,
      default: 400,
    },
    cssClasses: {
      default: "",
      type: String,
    },
    styles: {
      type: Object,
      default: () => {},
    },
    plugins: {
      type: Object,
      default: () => {},
    },
    chartType: {
      type: String,
    },
  },
  components: {
    Doughnut,
    Bar,
    Line,
  },
});
</script>