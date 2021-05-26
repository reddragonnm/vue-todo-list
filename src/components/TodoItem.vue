<template>
  <div class="todo">
    <TodoItemCheckbox @checkbox-toggle="$emit('todo-done-toggle')" />

    <p :class="{ done }">{{ text }}</p>

    <i @click="$emit('remove-todo')" class="far fa-trash-alt delete-icon"></i>
  </div>
</template>

<script>
  import TodoItemCheckbox from "./TodoItemCheckbox";

  export default {
    name: "TodoItem",

    components: {
      TodoItemCheckbox,
    },

    props: {
      text: String,
      done: Boolean,
    },
  };
</script>

<style scoped>
  .todo {
    width: 60%;

    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    border: 2px solid rgba(150, 150, 150, 0.4);
    border-radius: 30px;

    margin: 30px auto;
    padding: 25px;

    transition: all 0.2s ease;
  }

  .todo:hover {
    box-shadow: 5px 5px greenyellow;
  }

  .done {
    text-decoration: line-through;
  }

  p {
    font-size: 20px;
  }

  .delete-icon {
    cursor: pointer;
    transition: all 0.2s ease;
  }

  .delete-icon:hover {
    transform: scale(1.2);
  }
</style>
