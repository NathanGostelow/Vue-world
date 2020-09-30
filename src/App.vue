<template>
  <div id="app">
    <h1 class="app-title">TODO APP</h1>
    <todo-list />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
export default {
  name: "App",
  components: {
    TodoList,
  },
  data: function() {
    return {
      inputMessage: "",
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #d90368;
  margin-top: 60px;
}

.app-title {
  color: #d90368;
  font-size: 48px;
}
</style>
