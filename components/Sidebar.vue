<template>
  <aside
    class="z-20 hidden w-64 overflow-y-auto bg-white dark:bg-gray-800 md:block flex-shrink-0"
  >
    <div class="py-4 text-gray-500 dark:text-gray-400">
      <NuxtLink
        class="ml-6 text-lg font-bold text-gray-800 dark:text-gray-200"
        to="/"
      >
        Sun tracker
      </NuxtLink>
    </div>

    <span v-for="element in menuElements" :key="element.menu">
      <NuxtLink :to="element.link">
        <div class="relative px-6 py-3" @click="toggleSelectedElement(element)">
          <span
            v-if="element.isActive"
            class="absolute inset-y-0 left-0 w-1 bg-yellow-500 rounded-tr-lg rounded-br-lg"
            aria-hidden="true"
          ></span>
          <span
            class="inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200"
            :class="{ 'text-gray-800 dark:text-gray-100': element.isActive }"
          >
            <span class="m-1">{{ element.menu }}</span>
          </span>
        </div>
      </NuxtLink>
    </span>
  </aside>
</template>

<script lang="ts">
type MenuElement = {
  menu: string;
  link: string;
  isActive: boolean;
};

export default defineComponent({
  data() {
    return {
      menuElements: [
        {
          menu: "Customer",
          link: "/customer",
          isActive: false,
        },
        {
          menu: "Suplement",
          link: "/suplement",
          isActive: false,
        },
        {
          menu: "Nutrient",
          link: "/nutrient",
          isActive: false,
        },
        {
          menu: "Intake",
          link: "/intake",
          isActive: false,
        },
        {
          menu: "Tests",
          link: "/tests",
          isActive: false,
        },
      ],
      activeLink: false,
    };
  },
  methods: {
    toggleSelectedElement(menuElement: MenuElement): void {
      this.menuElements.forEach((menu) => {
        menu.isActive = false;
      });
      menuElement.isActive = true;
    },
  },
});
</script>
 
 