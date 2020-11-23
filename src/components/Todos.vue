<template>
  <div>
    <h1>Todos</h1>

    <div v-bind:key="todo.id" v-for="todo in todos">
      <Todo v-bind:todo="todo"/>
    </div>
  </div>
</template>

<script>
import Todo from './Todo.vue';

export default {
  name: "Todos",
  props: ["todos"],
  components: {Todo},
};
</script>

<style scoped>
</style>