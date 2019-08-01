<template>
<div id ="app">
  <Header />
  <AddTodo v-on:add-todo="addTodo"/>
  <Todos v-bind:todos="todos" v-on:del-todo="deletetask" /> 
  <ul>
    <li>
      <h3>Active</h3>
      <p>{{ activeTasks.length }}</p>
    </li>
    <li>
      <h3>Complete</h3>
      <p>{{ completedTasks.length }}</p>
    </li>
    <li>
      <h3>Total</h3>
      <p>{{ todos.length }}</p>
    </li>
  </ul>
</div>

    
</template>
<script>

import Header from './components/Layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'app',
  components:{
    Header,
    Todos,
    AddTodo 
  },
  data() {
    return {
   
      todos: [
        {
          id: 1,
          title: "Task one",
          completed: false
        },  
        {
           id: 2,
          title: "Task two",    
          completed: false
        },
         {
           id: 3,
          title: "Task three",
          completed: false
        }
      ]

    }

  },
  
  computed: {
    activeTasks() {
      function isTaskActive() {
        return !task.completed
      }

      return this.todos.filter(isTaskActive)
    },

    completedTasks() {
      function isTaskComplete() {
        return task.completed
      }

      return this.todos.filter(isTaskComplete)
    }
  },
  methods: {
    deletetask(id) {
      this.todos = this.todos.filter(todo =>  todo.id !== id);
    },
    addTodo(newTodo){
      newTodo.id = this.todos.length+1;
      this.todos.push(newTodo);
    }
  }
   
}
</script>

<style >
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
 .btn{
   display: inline-block;
   border: none;
   background: green;
   color:#fff;
   padding: 7px 20px;
   cursor: pointer;
 }

 .btn-hover {
   background: #666;
 }
</style>

