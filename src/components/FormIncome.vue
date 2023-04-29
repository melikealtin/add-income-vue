<template>
  <form @submit.prevent="formHandler">
    <input type="text" placeholder="Description..." v-model="formData.desc" />
    <input type="number" placeholder="Value..." v-model="formData.value" />
    <input type="date" placeholder="Date..." v-model="formData.date" />
    <input type="submit" value="SEND" />
  </form>
</template>

<script>
import { reactive } from "vue";
export default {
  props: {
    state: Object,
  },

  setup(props, { emit }) {
    const formData = reactive({
      desc: null,
      value: null,
      date: null,
    });

    function formHandler() {
      emit("add-income", {
        desc: formData.desc,
        value: formData.value,
        date: formData.date,
      });
      formData.desc = null;
      formData.value = null;
      formData.date = null;
    }

    return {
      formData,
      formHandler,
    };
  },
};
</script>

<style lang="scss">
form {
  display: flex;
  justify-content: center;
  margin-top: 30px;
  input {
    color: #16132f;
    border: none;
    outline: none;
    font-size: 20px;
    &::placeholder {
      color: #aaa;
    }
    &:not([type="submit"]) {
      display: block;
      background: #fff;
      border: none;
      outline: none;
      padding: 5px 15px;
    }
    &:first-of-type {
      border-radius: 8px 0px 0px 8px;
    }
    &:last-of-type {
      border-radius: 0px 8px 8px 0px;
    }
  }
  input[type="submit"] {
    display: block;
    background: none;
    border: none;
    outline: none;
    color: #fff;
    font-weight: 500;
    text-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);
    padding: 5px 15px;
    background-color: #6b91f7;
    cursor: pointer;
  }
}
</style>
