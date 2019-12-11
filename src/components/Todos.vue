<template>
  <div class="todos">
    <div v-bind:key="todo.id" v-for="todo in todos" class="todoItems">
      <TodoItem
        v-bind:todo="todo"
        v-on:delete-todo="$emit('delete-todo', todo.id)"
      />
    </div>

    <!-- To Loop through the data use another directive VFor  -->
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
  name: 'Todos',
  components: {
    TodoItem
  },
  props: ['todos']
}
</script>

<style scoped></style>
