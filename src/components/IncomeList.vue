<template>
  <div class="income-list">
    <income-item
      v-for="data in state.sortedIncome"
      :key="data.id"
      :income="data"
      :deleteItem="deleteItem"
    />
  </div>
</template>

<script>
import IncomeItem from "./IncomeItem.vue";

export default {
  components: { IncomeItem },
  props: {
    state: Object,
    deleteItem: Function,
  },
  setup() {
    return {
      IncomeItem,
    };
  },
};
</script>

<style scoped lang="scss">
.income-list {
  margin-top: 30px;
  padding: 15px;
}
</style>
