<template>
  <div class="todo-list">
    <div class="todo-list-input-container">
      <input class="todo-list-input" v-model="newMessageTitle" />
      <button v-on:click="addTodo">Add Todo</button>
    </div>
    <todo-item
      v-for="item in listOfTodos"
      v-bind:item="item"
      v-bind:key="item.id"
      v-on:removeTodo="removeTodo"
    >
    </todo-item>
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
      newMessageTitle: "",
    };
  },
  methods: {
    addTodo: function() {
      const newId = this.listOfTodos.length;
      if (this.newMessageTitle.length === 0) return null;
      this.listOfTodos.push({
        id: newId,
        title: this.newMessageTitle,
      });
      this.newMessageTitle = "";
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
