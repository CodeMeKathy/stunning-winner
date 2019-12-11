<template>
  <div id="app">
    <!-- V Bind allows data to be passed through to components as props. -->
    <!-- There are many types of template directives -->

    <Header />
    <!-- Use v-on to catch the child component emit -->
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layout/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'

import axios from 'axios'

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    AddTodo
  },

  // data is function returning an object
  data() {
    return {
      todos: [
        //   {
        //     id: '1',
        //     title: 'Clean Kitchen',
        //     completed: 'false'
        //   },
        //   {
        //     id: '2',
        //     title: 'Laundry',
        //     completed: 'false'
        //   },
        //   {
        //     id: '3',
        //     title: 'Complete Vue Crash Course',
        //     completed: 'false'
        //   },
        //   {
        //     id: '4',
        //     title: 'Complete React ZTM',
        //     completed: 'false'
        //   },
        //   {
        //     id: '5',
        //     title: 'Git Sh*t Done',
        //     completed: 'false'
        //   }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos${id}`)
        // eslint-disable-next-line no-unused-vars
        .then(res => (this.todos = this.todos.filter(todo => todo.id !== id)))
        // eslint-disable-next-line no-console
        .catch(error => console.log(error))
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo

      axios
        .post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
        .then(res => (this.todos = [...this.todos, res.data]))
        // eslint-disable-next-line no-console
        .catch(error => console.log(error))
    }
  },
  created() {
    axios
      .get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => (this.todos = res.data))
      // eslint-disable-next-line no-console
      .catch(error => console.log(error))
  }
}
</script>

// Global Stying
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
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
