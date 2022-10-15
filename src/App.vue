<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <MisTareas title="Primera tarea"></MisTareas>
  <MisTareas title="Segunda tarea"></MisTareas>
</template>

<script>
import MisTareas from './components/ToDo.vue'

export default {
  name: 'App',
  components: {
    MisTareas
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
