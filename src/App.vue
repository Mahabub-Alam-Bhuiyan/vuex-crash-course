<template>
  <div id="app">
    <AddTodos />
    <filter-todos />
    <Todos />
  </div>
</template>

<script>
import Todos from './components/Todos'
import AddTodos from "@/components/AddTodos";
import FilterTodos from "@/components/FilterTodos";

export default {
  name: 'App',
  components: {
    FilterTodos,
    AddTodos,
    Todos
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin: 60px 30px 0 60px;
}
</style>
