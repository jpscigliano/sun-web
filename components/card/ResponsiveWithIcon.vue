<template>
  <div
    class="flex items-center p-4 bg-white rounded-lg shadow-xs dark:bg-gray-800"
  >
    <div :class="svgClass">
      <element-svg
        :class="'w-5 h-5'"
        :view-box="'0 0 20 20'"
        :fill="'currentColor'"
        :pic="svgPic"
      />
    </div>

    <div>
      <p class="mb-2 text-sm font-medium text-gray-600 dark:text-gray-400">
        {{ title }}
      </p>
      <p class="text-lg font-semibold text-gray-700 dark:text-gray-200">
        {{ content }}
      </p>
    </div>
  </div>
</template>

<script lang="ts">
export default defineComponent({
  props: {
    svgClass: {
      type: String,
      required: true,
    },
    svgPic: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    content: {
      type: String,
      required: true,
    },
  },
});
</script>