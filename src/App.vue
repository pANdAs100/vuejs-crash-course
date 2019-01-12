<template>
  <div id="app">
    <!-- v-bind directive passes todos(in data) to Todos.vue component -->
    <!-- v-on catched the emited delete todo event -->
    <Header />
    <!-- catch the emit for the new todo -->
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'app',
  components: {
    // make sure to add all compponents in export
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: false
        },
        {
          id: 3,
          title: "Sometimes I like to diverge",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id){
      // set this.todos to current todos.filter(arr => todo.id != id)
      this.todos = this.todos.filter(todo => todo.id != id);
    },
    addTodo(newTodo) {
      console.log('add todo');
      this.todos = [...this.todos, newTodo];
    }
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
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>
