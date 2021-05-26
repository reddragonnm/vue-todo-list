<template>
  <div :class="{ heading: true, 'full-heading': todosEmpty }">
    <h1>Todo List</h1>
    <input
      type="text"
      v-model="newTodoText"
      :placeholder="
        todosEmpty ? 'Add a new todo to get started!' : 'Add a new todo!'
      "
      @keyup.enter="newTodo"
    />
  </div>
</template>

<script>
  export default {
    name: "TodoHeading",

    data() {
      return {
        newTodoText: "",
      };
    },

    props: {
      todosEmpty: Boolean,
    },

    methods: {
      newTodo() {
        this.$emit("new-todo", this.newTodoText);
        this.newTodoText = "";
      },
    },
  };
</script>

<style scoped>
  .heading {
    height: 250px;

    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;

    background: beige;

    transition: all 0.5s ease;
  }

  .full-heading {
    height: 100vh;
    justify-content: center;
    gap: 30px;
  }

  input {
    width: 60%;
    padding: 5px;

    outline: none;
    background: transparent;
    border: 5px solid lightcoral;

    font-size: 25px;
    text-align: center;
  }

  h1 {
    font-size: 50px;

    background: url("data:image/svg+xml;charset=utf8,%3Csvg version='1.1' xmlns='http://www.w3.org/2000/svg' x='0px' y='0px' width='1px' height='1px' viewBox='0 0 1 1' preserveAspectRatio='none'%3E%3Crect x='0' y='0' width='1' height='1' fill='dodgerblue' /%3E%3C/svg%3E")
      no-repeat 100% 100%;
    background-size: 100% 30%;
  }
</style>
