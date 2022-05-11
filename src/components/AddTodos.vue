<template>
<div class="container">
  <form @submit.prevent="TodosAdd()">
    <input type="text" v-model="title" placeholder="add todo">
    <input type="number" v-model="id" placeholder="add todo id">
    <input type="number" v-model="userId" placeholder="add todo userId">
    <input type="submit" value="submit">
  </form>
</div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "AddTodos",
  data(){
    return{
      title:'',
      id:'',
      userId:''
    }
  },
  methods:{
    ...mapActions(['addTodo']),
    TodosAdd(){
      this.addTodo(this.userId , this.title),
      this.title='',
      this.id=''
    }
  },

}
</script>

<style scoped>
form{
  display: flex;
}
input[type="text"]{
  flex: 7;
  padding: 10px;
  border: 1px solid #2c3e50;
  outline: 0;
}
input[type="number"]{
  flex: 3;
  padding: 10px;
  border: 1px solid #2c3e50;
  outline: 0;
}
input[type="submit"] {
  flex: 2;
  padding: 10px;
  background-color: #2c3e50;
  border: 1px solid #2c3e50;
  color: white;
  cursor: pointer;
}
.container{
  margin-right: 60px;
}
</style>