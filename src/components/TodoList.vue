<template>
  <div class="todo-list">
    <div class="todo-list-input-container">
      <input class="todo-list-input" v-model="skeletonTodoItem.title" />
      <button v-on:click="addTodo">Add Todo</button>
    </div>
    <todo-item
      v-for="item in listOfTodos"
      v-bind:item="item"
      v-bind:key="item.id"
      v-on:removeTodo="removeTodo"
    >
    </todo-item>
    <todo-item v-bind:item="skeletonTodoItem"> </todo-item>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "TodoList",
  components: { TodoItem },
  data: function() {
    return {
      listOfTodos: [
        { id: 0, title: "message 1" },
        { id: 1, title: "message 2" },
      ],
      skeletonTodoItem: { id: null, title: "", isSkeleton: true },
    };
  },
  methods: {
    addTodo: function() {
      const newId = this.listOfTodos.length;
      if (this.skeletonTodoItem.title.length === 0) return null;
      this.skeletonTodoItem.id = newId;
      this.skeletonTodoItem.isSkeleton = false;
      this.listOfTodos.push(this.skeletonTodoItem);
      this.skeletonTodoItem = { id: null, title: "", isSkeleton: true };
    },
    removeTodo: function(event) {
      this.listOfTodos.splice(this.listOfTodos.indexOf(event), 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todo-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.todo-list-input {
}
.todo-list-input-container {
  margin-bottom: 12px;
}
</style>
