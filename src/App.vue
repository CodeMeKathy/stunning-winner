<template>
  <div id="app">

    {{msg}}

  </div>
</template>

<script>

export default {
  name: 'app',
  components: {
    
  },

  // data is function returning an object
  data() {
    return {
      msg: 'Hello'
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
