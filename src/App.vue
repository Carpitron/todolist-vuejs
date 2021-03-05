<template>
  <div id="app">
    <task v-bind:tasks="tasks"></task>
  </div>
</template>

<script>
import Task from "./components/todo-card";

export default {
  name: "App",
  components: {
    Task,
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: "Faire les courses",
          completed: false,
        }
      ],
    };
  },
};
</script>

<style>
body{
  background-color: #ffd34c;
}
</style>