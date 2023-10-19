
<script setup>
import { defineProps, ref, computed } from "vue";
const value = ref(props.value);
const min = ref(props.min);
const max = ref(props.max);

const statusColor = computed(() => {
  if (value.value >= min.value && value.value <= max.value) {
    return "#86efac";
  } else {
    return "#fca5a5";
  }
});

const statusLocation = computed(() => {
  if (value.value >= min.value && value.value <= max.value) {
    return 50;
  } else {
    return 25;
  }
});

const props = defineProps({
  value: String,
  min: String,
  max: String,
});
</script>

<template>
  <div>
    <!-- VALUE -->
    <div
      :style="{
        position: 'relative',
        left: statusLocation + '%',
      }"
      class="mb-2 flex flex-nowrap text-xs"
    >
      <span
        :style="{
          position: 'relative',
          'background-color': statusColor,
        }"
        style="min-width: 30px"
        class="px-0 py-0 font-semibold rounded"
        >{{ value }}</span
      >
      <span class="triangle"></span>
    </div>
    <!-- PROGRESS BAR -->
    <div style="position: relative; left: 15px">
      <div class="overflow-hidden h-1 text-xs flex rounded">
        <div
          style="width: 27%"
          class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-red-400"
        />
        <div
          style="width: 46%"
          class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-green-400"
        />
        <div
          style="width: 27%"
          class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-red-400"
        />
      </div>

      <!-- <div class="relative flex">
        <div style="left: 27%" class="relative -ml-1">
          <span>{{ min }}</span>
        </div>
        <div style="left: 73%" class="absolute -ml-1">
          <span>{{ max }}</span>
        </div>
      </div> -->
    </div>
  </div>
</template>



<style scoped>
span {
  text-align: center;
  font-size: 8px;
}

.triangle {
  display: block;
  height: 0px;
  width: 0px;
  border: 8px solid transparent;
  border-top-color: v-bind(statusColor);
  position: absolute;
  bottom: -15px;
  transform: translateX(50%);
}
</style>