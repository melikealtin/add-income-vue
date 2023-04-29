<template>
  <div class="income-item">
    <div class="removeitem">
      <span class="remove" @click="deleteItem(income)">
        <svg
          class="remove"
          xmlns="http://www.w3.org/2000/svg"
          height="20"
          viewBox="0 96 960 960"
          width="20"
        >
          <path
            d="m249 849-42-42 231-231-231-231 42-42 231 231 231-231 42 42-231 231 231 231-42 42-231-231-231 231Z"
          />
        </svg>
      </span>
    </div>
    <div class="desc">{{ income.desc }}</div>
    <div class="price">${{ income.value }}</div>
    <div class="date">{{ formattedDate }}</div>
  </div>
</template>

<script>
export default {
  props: {
    income: Object,
    deleteItem: Function,
  },
  setup(props) {
    let date = new Date(props.income.date);
    let day = date.getDate();
    let month = date.getMonth();
    let year = date.getFullYear();

    let formattedDate = day + "/" + month + "/" + year;

    return {
      formattedDate,
    };
  },
};
</script>

<style lang="scss" scoped>
.income-item {
  position: relative;
  display: flex;
  padding: 15px 15px 15px 0px;
  background-color: #fff;
  border-radius: 8px;
  max-width: 600px;
  margin: 0 auto 15px;
}
.removeitem {
  .remove {
    color: #ef2d2d;
    svg {
      font-weight: 700;
      font-size: 20px;
      text-align: center;
      margin: 2px 15px;
      cursor: pointer;
    }
  }
}
.desc {
  color: #16132f;
  flex: 1 1 100%;
  font-size: 20px;
}
.price {
  color: #16132f;
  min-width: 100px;
  font-size: 20px;
}
.date {
  color: #16132f;
  text-align: right;
  font-size: 20px;
}
</style>
