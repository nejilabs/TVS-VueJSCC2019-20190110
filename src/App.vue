<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-Todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
// Imports
import Header from "./components/layout/Header.vue";
import Todos from "./components/Todos.vue";
import AddTodo from "./components/AddTodo.vue";
import axios from "axios";

export default {
  name: "app",

  // Components
  components: {
    Header,
    Todos,
    AddTodo,
  },

  // Data Examples
  data() {
    return {
      todos: [],
    };
  },

  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },

    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => console.log(err));
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>