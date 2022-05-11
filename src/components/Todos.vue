4<template>
<div>
  <h3>Todos</h3>
  <div class="legend">
    <span> Double click for mark as complete </span>
    <span> <span class="incomplete"> </span> In Complete </span>
    <span> <span class="complete"> </span> Complete </span>
  </div>
  <div class="full-todo">

    <div v-for="todos in allTodos"
         :key="todos.id"
         class="todos"
         @click="doubleClick(todos)"
         :class="{'is-complete':todos.completed}"
    >
      <span class="cross" @click="deleteTodo(todos.id)"> 	&#10060; </span>
      <p> {{todos.id}} </p>
      <p> {{todos.userId}} </p>
      <p> {{ todos.title }} </p>

    </div>
  </div>
</div>
</template>

<script>
import { mapGetters , mapActions } from 'vuex'
export default {
  // eslint-disable-next-line
name: "Todos",
  methods:{
  ...mapActions(["fetchTodos", "deleteTodo","updateTodo" ]),
    doubleClick(todos){
      const updTodo = {
        id: todos.id,
        title: todos.title,
        userId: todos.userId,
        completed: !todos.completed
      }
    this.updateTodo(updTodo)
    }
  },
  computed: mapGetters(['allTodos']),
  created() {
    this.fetchTodos();
  }
}
</script>

<style scoped>
.full-todo{
  display: grid;
  grid-template-columns: repeat(4 , 1fr);
  grid-gap: 1rem;
}
.todos{
  width: 200px;
  margin: 10px;
  border: 1px solid black;
  border-radius: 5px;
  background-color: #2c3e50;
  color: white;
  position: relative;
  padding: 10px;
  cursor: pointer;
}
.cross{
  position: absolute;
  top: 0;
  right: 0;
  padding: 3px;
  cursor: pointer;
  background-color: #c3c5c7;
  border-radius: 5px;
}
.legend{
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}
.complete{
  display: inline-block;
  height: 10px;
  width: 10px;
  background-color: #045e04;
}
.is-complete{
  background-color: #045e04;
}
.incomplete{
  display: inline-block;
  height: 10px;
  width: 10px;
  background-color: #2c3e50;
}
</style>