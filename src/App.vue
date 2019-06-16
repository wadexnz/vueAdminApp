<template>
  <div>
    <header class="navbar">
      <div class="container">
        <h1><a href="index.html">Vue User Admin</a></h1>
      </div>
    </header>
    <usersList></usersList>
  </div>
</template>

<script>
  import UsersList from './components/UsersList.vue'

  export default {
    name: 'app',
    components: {
      UsersList
    }
  }
</script>

<style scoped>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 0px;
    padding: 0px;
  }
  .navbar {
    background-color: white
  }
</style>
