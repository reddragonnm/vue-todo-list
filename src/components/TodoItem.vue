<template>
  <div class="todo">
    <TodoItemCheckbox
      :checkedInit="done"
      @checkbox-toggle="$emit('todo-done-toggle')"
    />

    <p :class="{ done }">{{ text }}</p>

    <i @click="$emit('remove-todo')" class="fas fa-trash-alt delete-icon"></i>
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
  p {
    font-size: 30px;
  }

  i {
    font-size: 20px;
  }

  .todo {
    background: white;
    width: 50%;
    user-select: none;

    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    border: 2px solid rgba(150, 150, 150, 0.4);
    border-radius: 25px;

    margin: 30px auto;
    padding: 20px;

    transition: all 0.2s ease;
  }

  .todo:hover {
    box-shadow: 5px 5px greenyellow;
  }

  .done {
    text-decoration: line-through;
  }

  .delete-icon {
    cursor: pointer;
    transition: all 0.2s ease;
  }

  .delete-icon:hover {
    transform: scale(1.2);
  }
</style>
