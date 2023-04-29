<template>
  <div>
    <header-income :totalIncome="state.totalIncome" />
    <form-income @add-income="AddIncome" />
    <income-list :state="state" :deleteItem="deleteItem" />
  </div>
</template>

<script setup>
import { reactive, computed } from "vue";
import HeaderIncome from "./components/HeaderIncome.vue";
import FormIncome from "./components/FormIncome.vue";
import IncomeList from "./components/IncomeList.vue";

const state = reactive({
  income: [],
  totalIncome: computed(() => {
    let temp = 0;

    if (state.income.length > 0) {
      for (let i = 0; i < state.income.length; i++) {
        temp += state.income[i].value;
      }
    }
    return temp;
  }),
  sortedIncome: computed(() => {
    let temp = [];
    temp = state.income.sort(function (a, b) {
      return b.date - a.date;
    });
    return temp;
  }),
});

function AddIncome(data) {
  let d = data.date.split("-");
  let newD = new Date(d[0], d[1], d[2]);

  state.income = [
    ...state.income,
    {
      id: Date.now(),
      desc: data.desc,
      value: parseInt(data.value),
      date: newD.getTime(),
    },
  ];
  console.log(state.income);
}
function deleteItem(data) {
  console.log("data", data);
  state.income = state.income.filter((t) => t !== data);
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}

body {
  background-color: #f0f1f2;
}
</style>
