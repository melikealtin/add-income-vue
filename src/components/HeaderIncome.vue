<template>
  <header>
    <h1>Add Income</h1>
    <div class="total-income">${{ totalIncome }}</div>
  </header>
</template>

<script>
export default {
  props: {
    totalIncome: Number,
  },
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px 30px;
  background-color: #fff;
  border-bottom: 4px solid #6b91f7;
  h1 {
    color: #16132f;
    font-size: 28px;
  }
  .total-income {
    font-family: Arial, Helvetica, sans-serif;
    background-color: #6b91f7;
    color: #fff;
    font-size: 20px;
    font-weight: 900;
    padding: 5px 10px;
    min-width: 100px;
    text-align: center;
    border-radius: 8px;
    box-shadow: inset 0px 0px 6px rgba(0, 0, 0, 0.25);
    text-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25);
  }
}
</style>
