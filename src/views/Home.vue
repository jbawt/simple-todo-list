<template>
  <div class="main-page" id="app">
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>

import AddTodo from '../components/AddTodo'
import Todos from '../components/Todos';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`http://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(error => console.log(error))
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios.post('http://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(error => console.log(error))
    }
  },
  created() {
    axios.get('http://jsonplaceholder.typicode.com/todos?_limit=10')
      .then((res) => {
        this.todos = res.data
      })
      .catch((error) => console.log(error))
  }
}
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
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }

  .main-page {
    margin-top: 20px;
  }
</style>

