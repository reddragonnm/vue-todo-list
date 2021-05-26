<template>
  <div>
    <div class="todos" v-for="(todo, index) in todos" :key="index">
      <TodoItem
        :text="todo.text"
        :done="todo.done"
        @todo-done-toggle="toggleTodo(index)"
        @remove-todo="removeTodo(index)"
      />
    </div>
  </div>
</template>

<script>
  import TodoItem from "./components/TodoItem";

  export default {
    name: "App",

    data() {
      return {
        todos: [],
      };
    },

    created() {
      this.addTodo("hello");
      this.addTodo("world");
    },

    methods: {
      addTodo(text) {
        this.todos.unshift({ text: text, done: false });
      },

      toggleTodo(index) {
        this.todos[index].done = !this.todos[index].done;
      },

      removeTodo(index) {
        this.todos.splice(index, 1);
      },
    },

    components: {
      TodoItem,
    },
  };
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: sans-serif;
  }
</style>
