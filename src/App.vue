<template>
  <s-table row-key="key" :data-source="dataSource" @change="handleTableChange">
    <s-table-column title="Name" data-index="name">
      <template #title>21232123123</template>
    </s-table-column>

    <s-table-column-group title="Score">
      <s-table-column
        title="Chinese"
        data-index="chinese"
        :onSort="handleSort('chinese')"
      >
        <template #default="{ value, record }">
          {{ value }}--{{ record.name }}
        </template>
        <template #title>test title slot</template>
      </s-table-column>
      <s-table-column
        title="Math"
        data-index="math"
        :onSort="handleSort('math')"
      />
      <s-table-column
        title="English"
        data-index="english"
        :onSort="handleSort('english')"
      />
    </s-table-column-group>
  </s-table>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import STable from "./components/SimpleTable/index.vue";
import {
  STableColumn,
  STableColumnGroup,
} from "./components/SimpleTable/index.vue";

export default defineComponent({
  name: "App",
  components: {
    STable,
    STableColumn,
    STableColumnGroup,
  },
  setup() {
    const dataSource = ref<object[]>(
      [
        {
          key: "1",
          name: "John Brown",
          chinese: 98,
          math: 60,
          english: 70,
        },
        {
          key: "2",
          name: "Jim Green",
          chinese: 98,
          math: 66,
          english: 89,
        },
        {
          key: "3",
          name: "Joe Black",
          chinese: 98,
          math: 90,
          english: 70,
        },
        {
          key: "4",
          name: "Jim Red",
          chinese: 88,
          math: 99,
          english: 89,
        },
      ]
      // Array.from({ length: 50 }, (_, i) => ({
      //   key: i,
      //   name: `Jim Red---${i}`,
      //   chinese: 88,
      //   math: 99,
      //   english: 89,
      // }))
    );
    const handleTableChange = () => {};
    const handleSort = (type: string) => {
      return function (a: any, b: any) {
        return a[type] - b[type];
      };
    };
    return {
      dataSource,
      handleTableChange,
      handleSort,
    };
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
