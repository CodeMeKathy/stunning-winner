<template>
  <div>
    <form @submit="addTodo">
      <!-- The data needs to be travered up to the parent -->
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add New Todo"
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
import uuid from 'uuid'

export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault()
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      }
      // Send to parent via emitting an event
      this.$emit('add-todo', newTodo)
      this.title = ''
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
}
input[type='text'] {
  flex: 10;
  padding: 5px;
}
input[type='submit'] {
  flex: 2;
}
</style>
