<template>
  <div>
    <TodoHeading :todosEmpty="todos.length == 0" @new-todo="newTodo" />

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
  import TodoHeading from "./components/TodoHeading";

  export default {
    name: "App",

    components: {
      TodoItem,
      TodoHeading,
    },

    data() {
      return {
        todos: [],
      };
    },

    created() {
      const todos = localStorage.getItem("todos");
      if (todos) {
        this.todos = JSON.parse(todos);
      }
    },

    methods: {
      updateStorage() {
        localStorage.setItem("todos", JSON.stringify(this.todos));
      },

      newTodo(text) {
        this.todos.push({ id: this.todos.length, text: text, done: false });
        this.updateStorage();
      },

      toggleTodo(id) {
        this.todos = this.todos.map((obj) =>
          obj.id == id ? { ...obj, done: !obj.done } : obj
        );

        this.updateStorage();
      },

      removeTodo(id) {
        this.todos = this.todos.filter((obj) => obj.id != id);
        this.updateStorage();
      },
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

  /* custom scrollbar */
  ::-webkit-scrollbar {
    width: 20px;
  }

  ::-webkit-scrollbar-track {
    background-color: transparent;
  }

  ::-webkit-scrollbar-thumb {
    background-color: #d6dee1;
    border-radius: 20px;
    border: 6px solid transparent;
    background-clip: content-box;
  }

  ::-webkit-scrollbar-thumb:hover {
    background-color: #a8bbbf;
  }
</style>
