<template>
  <div class="min-w-0 p-4 bg-white rounded-lg shadow-xs dark:bg-gray-800">
    <chart-title :title="title" />
    <chart-canvas v-bind="chartConfig" />
  </div>
</template>

<script lang="ts">
export default defineComponent({
  props: {
    title: {
      type: String,
      default: "",
    },
    chartConfig: {
      type: Object,
    },
  },
});
</script>