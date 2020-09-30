<template>
  <div class="todo">
    <div class="todo-title">
      {{ item.title }}
    </div>
    <button class="todo-button" v-on:click="$emit('removeTodo', item)">
      -
    </button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    item: Object,
    removeTodo: Function,
  },
};
</script>

<style scoped>
.todo {
  width: 750px;
  border-radius: 10px;
  background-color: #d90368;
  color: white;
  display: flex;
  justify-content: space-between;
  min-height: 50px;
  margin-bottom: 12px;
}
.todo-button {
  width: 50px;
  background-color: white;
  border: 1px solid #d90368;
  border-bottom-right-radius: 10px;
  border-top-right-radius: 10px;
  color: #d90368;
}
.todo-title {
  padding: 12px;
}
</style>
