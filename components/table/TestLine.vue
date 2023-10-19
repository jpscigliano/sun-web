<template>
  <tr class="text-gray-700 dark:text-gray-400">
    <td :class="columnClass">
      <div class="flex items-center text-sm">
        <div>
          <p class="font-semibold">{{ name }}</p>
          <p class="text-xs text-gray-600 dark:text-gray-400">
            {{ description }}
          </p>
        </div>
      </div>
    </td>
    <!-- AMOUNT  -->
    <td :class="columnClass" class="text-sm">{{ amount }} {{ unit }}</td>

    <!-- STATUS  -->
    <td :class="columnClass" class="text-xs">
      <CustomTestResult
        style="min-width: 100px"
        :min="range?.min"
        :max="range?.max"
        :value="amount"
      />
    </td>
    <!-- RANGE  -->
    <td :class="columnClass" class="text-sm" :min="10" :max="20" :value="40">
      {{ range?.min }} - {{ range?.max }} {{ unit }}
    </td>
    <!-- DATE  -->
    <td :class="columnClass" class="text-sm font-medium">
      {{ date }}
    </td>
    <!-- DAYS PASSED  -->
    <td :class="columnClass" class="text-xs">
      <span
        class="px-2 py-1 font-semibold leading-tight rounded-full"
        :class="daysPassedClasses"
      >
        {{ daysPassed }} days
      </span>
    </td>
    <!-- ACTIONS  -->
    <td :class="columnClass">
      <div class="flex items-center space-x-4 text-sm" v-if="hasAction">
        <div
          class="flex items-center justify-between px-2 py-2 text-sm font-medium leading-5 text-purple-600 rounded-lg dark:text-gray-400 focus:outline-none focus:shadow-outline-gray"
          aria-label="Edit"
        />
        <div
          class="flex items-center justify-between px-2 py-2 text-sm font-medium leading-5 text-purple-600 rounded-lg dark:text-gray-400 focus:outline-none focus:shadow-outline-gray"
          aria-label="Delete"
        />
      </div>
    </td>
  </tr>
</template>

<script lang="ts">
export default defineComponent({
  data() {
    return {
      columnClass: "px-4 py-3",
      columnClassSmall: "px-1 py-3",
      statusClasses: {
        "text-green-700 bg-green-100 dark:bg-green-700 dark:text-green-100":
          this.status === "ok",
        "text-orange-700 bg-orange-100 dark:text-white dark:bg-orange-600":
          this.status === "low",
        "text-red-700 bg-red-100 dark:text-red-100 dark:bg-red-700":
          this.status === "high",
      },
      daysPassedClasses: {
        "text-red-700 bg-red-100 dark:text-red-100 dark:bg-red-700":
          this.daysPassed > 100,
      },
    };
  },
  props: {
    name: {
      type: String,
    },
    description: {
      type: String,
    },
    amount: {
      type: String,
    },
    unit: {
      type: String,
    },
    range: {
      type: Object,
    },
    status: {
      type: String,
      required: true,
    },
    date: {
      type: String,
    },
    daysPassed: {
      type: Number,
      default: 0,
    },
    hasAction: {
      type: Boolean,
      default: true,
    },
  },
});
</script>