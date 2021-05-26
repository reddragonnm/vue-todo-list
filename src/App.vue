<template>
  <div>
    <div class="todos" v-for="todo in todos" :key="todo.id">
      <TodoItem
        :text="todo.text"
        :done="todo.done"
        @todo-done-toggle="toggleTodo(todo.id)"
        @remove-todo="removeTodo(todo.id)"
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
      this.addTodo("world");
      this.addTodo("world");
      this.addTodo("world");
    },

    methods: {
      addTodo(text) {
        this.todos.push({ id: this.todos.length, text: text, done: false });
      },

      toggleTodo(id) {
        this.todos = this.todos.map((obj) => {
          if (obj.id == id) {
            return { ...obj, done: !obj.done };
          }
          return obj;
        });
      },

      removeTodo(id) {
        this.todos = this.todos.filter((obj) => obj.id != id);
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
