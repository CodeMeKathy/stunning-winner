
<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
      {{todo.title}}
      <button @click="$emit('delete-todo', todo.id)" class="delete">x</button>
      </p>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  // Methods are definged HERE within the export default export
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed
    }
  }
}
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.is-complete {
  text-decoration: line-through;
}
.delete {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
