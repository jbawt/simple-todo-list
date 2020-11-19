<template>
  <div class="items">
    <div class="todo-list" v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem'

export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
}
</script>

<style scoped>

  .items {
    border: 2px solid black;
    width: 80%;
    margin-left: 10%;
  }

  .todo-list:nth-of-type(even) {
    background: #4ac58edb;
  }
  
  .todo-list:nth-of-type(odd) {
    background: #f4f4f4;
  }
</style>