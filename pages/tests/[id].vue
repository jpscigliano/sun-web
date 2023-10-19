<script setup>
const lineConfig = {
  chartType: "Line",
  chartData: {
    labels: ["January", "February", "March", "April", "May", "June", "July"],
    datasets: [
      {
        label: "Organic",
        backgroundColor: "#0694a2",
        borderColor: "#0694a2",
        data: [43, 48, 40, 54, 67, 73, 70],
        fill: false,
      },
      {
        label: "Paid",
        fill: false,
        backgroundColor: "#7e3af2",
        borderColor: "#7e3af2",
        data: [24, 50, 64, 74, 52, 51, 65],
      },
    ],
  },
  chartOptions: {
    responsive: true,
    /**
     * Default legends are ugly and impossible to style.
     * See examples in charts.html to add your own legends
     *  */
    legend: {
      display: false,
    },
    tooltips: {
      mode: "index",
      intersect: false,
    },
    hover: {
      mode: "nearest",
      intersect: true,
    },
    scales: {
      x: {
        display: true,
        scaleLabel: {
          display: true,
          labelString: "Month",
        },
      },
      y: {
        display: true,
        scaleLabel: {
          display: true,
          labelString: "Value",
        },
      },
    },
  },
};
</script>

<template>
  <div class="container grid">
    <ElementPageTitle :page-title="'Vitamin D'" />

    <!-- Cards -->
    <div class="grid gap-6 mb-8 mt-5 md:grid-cols-2 xl:grid-cols-4">
      <CardResponsiveWithIcon
        :svg-pic="'people'"
        :svg-class="'p-3 mr-4 text-orange-500 bg-orange-100 rounded-full dark:text-orange-100 dark:bg-orange-500'"
        :title="'Current level'"
        :content="'45,68 mg/l'"
      />
      <CardResponsiveWithIcon
        :svg-pic="'cart'"
        :svg-class="'p-3 mr-4 text-blue-500 bg-blue-100 rounded-full dark:text-blue-100 dark:bg-blue-500'"
        :title="'Date'"
        :content="' 7 July 2023'"
      />
      <CardResponsiveWithIcon
        :svg-pic="'money'"
        :svg-class="'p-3 mr-4 text-green-500 bg-green-100 rounded-full dark:text-green-100 dark:bg-green-500'"
        :title="'Days since last test'"
        :content="'65 days'"
      />

      <CardResponsiveWithIcon
        :svg-pic="'message'"
        :svg-class="'p-3 mr-4 text-teal-500 bg-teal-100 rounded-full dark:text-teal-100 dark:bg-teal-500'"
        :title="'Something '"
        :content="'Its good to be alive'"
      />
    </div>

    <!-- Charts -->
    <ElementSectionTitle :section-title="'Evolution of parameter'" />
    <div class="grid gap-6 mb-8 md:grid-cols-2">
      <ChartWrapper :title="'Line'" :chart-config="lineConfig" />
    </div>
  </div>
</template>

