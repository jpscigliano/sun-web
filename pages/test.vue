<template>
  <PageContentPageTitle
    :page-title="'Latest blood test resut'"
  ></PageContentPageTitle>

  <div class="container grid">
    <div class="w-full mb-8 overflow-hidden rounded-lg shadow-xs">
      <div class="w-full overflow-x-auto">
        <table class="w-full whitespace-no-wrap">
          <TableHead :headers="tableHeaders" />
          <tbody
            class="bg-white divide-y dark:divide-gray-700 dark:bg-gray-800"
          >
            <TableTestLine
              v-for="test in tests"
              :key="test.name"
              :name="test.name"
              :description="test.description"
              :amount="test.amount"
              :unit="test.unit"
              :range="test.range"
              :status="test.status"
              :date="test.date"
              :daysPassed="test.daysPassed"
              :has-action="test.hasAction"
            />
          </tbody>
        </table>
      </div>
      <pagination-wrapper
        :total-elements="93"
        :current-page="3"
        :total-pages="10"
      />
    </div>
  </div>
</template>

<script lang="ts">
export default defineComponent({
  data() {
    return {
      tableHeaders: [
        "Parameter",
        "Value",
        "Status",
        "Range",
        "Date",
        "Day passed",
        "Actions",
      ],
      tests: [
        {
          name: "Vitamin D",
          description: "Calciferol",
          amount: 63.45,
          range: {
            min: 50,
            max: 60,
          },
          unit: "mg/l",
          status: "ok",
          daysPassed: "12",
          date: "11 September 2022",
          hasAction: true,
        },
        {
          name: "Vitamin C",
          description: "Calciferol",
          amount: 13,
          range: {
            min: 30,
            max: 45,
          },
          unit: "mg/l",
          status: "low",
          date: "31 July 2022",
          daysPassed: "120",
          hasAction: true,
        },
        {
          name: "Vitamin K",
          description: "Calciferol",
          amount: 26,
          range: {
            min: 20,
            max: 75,
          },
          unit: "mg/l",
          status: "ok",
          date: "19 November 2022",
          daysPassed: "2",
          hasAction: true,
        },
        {
          name: "Vitamin E",
          description: "Calciferol",
          amount: 45,
          range: {
            min: 33,
            max: 78,
          },
          unit: "mg/l",
          status: "high",
          date: "24 November 2023",
          daysPassed: "360",
          hasAction: true,
        },
        {
          name: "Vitamin D",
          description: "Calciferol",
          amount: 5,
          range: {
            min: 10,
            max: 110,
          },
          unit: "mg/l",
          status: "low",
          date: "5 August 2022",
          daysPassed: "79",
          hasAction: true,
        },
        {
          name: "Vitamin D",
          description: "Calciferol",
          amount: 3.25,
          range: {
            min: 20,
            max: 60,
          },
          unit: "mg/l",
          status: "low",
          date: "1 November 2023",
          daysPassed: "3200",
          hasAction: false,
        },
        {
          name: "Vitamin D",
          description: "Calciferol",
          amount: 12.05,
          range: {
            min: 50,
            max: 90,
          },
          unit: "mg/l",
          status: "ok",
          date: "12 April 2022",
          daysPassed: "182",
          hasAction: true,
        },
        {
          name: "Vitamin D",
          description: "Calciferol",
          amount: 31,
          range: {
            min: 28,
            max: 60,
          },
          unit: "mg/l",
          status: "high",
          date: "8 December 2023",
          daysPassed: "99",
          hasAction: false,
        },
      ],
    };
  },
});
</script>
 