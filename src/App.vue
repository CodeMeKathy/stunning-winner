<template>
  <div id="app">
    <!-- V Bind allows data to be passed through to components as props. -->
    <!-- There are many types of template directives -->
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from './components/Todos'

export default {
  name: 'app',
  components: {
    Todos
  },

  // data is function returning an object
  data() {
    return {
      todos: [
        {
          id: '1',
          title: 'Clean Kitchen',
          completed: 'true'
        },
        {
          id: '2',
          title: 'Laundry',
          completed: 'false'
        },
        {
          id: '3',
          title: 'Complete Vue Crash Course',
          completed: 'true'
        },
        {
          id: '4',
          title: 'Complete React ZTM',
          completed: 'false'
        },
        {
          id: '5',
          title: 'Git Sh*t Done',
          completed: 'false'
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
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
</style>
