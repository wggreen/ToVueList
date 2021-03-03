<template>
  <div>
    <h3>ToDo List</h3>
    <h5>{{ itemsRemaining }}</h5>
    <div v-for="item in todos" :key="item.id">
      <todo-item :todo="item" @status-change="handleStatusChange" />
    </div>
  </div>
</template>

<script>
import { todoItems } from "../data";
import TodoItem from "./ToDoItem";

export default {
  components: { TodoItem },
  data() {
    return {
      todos: [...todoItems],
    };
  },
  methods: {
    handleStatusChange(item) {
      item.complete = !item.complete;
      console.log(item);
    },
  },
  computed: {
    itemsRemaining() {
      const remaining = this.todos.filter((t) => !t.complete);
      if (remaining == 0) {
        return "There are no items left to do today";
      } else {
        return `There are ${remaining.length} items left to do today`;
      }
    },
  },
};
</script>

<style></style>