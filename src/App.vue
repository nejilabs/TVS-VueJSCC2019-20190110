<template>
  <div id="app">
    <Todos v-bind:todos="todos" />
  </div>
</template>

<script>
// Imports
import Todos from "./components/Todos";

export default {
  name: "app",

  // Components
  components: {
    Todos,
  },

  // Data Examples
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "todo One",
          completed: false,
        },
        {
          id: 2,
          title: "todo two",
          completed: true,
        },
        {
          id: 3,
          title: "todo three",
          completed: false,
        },
      ],
    };
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
</style>