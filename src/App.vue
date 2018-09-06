<template>
  <div class="todoList">
    <h1 class="header"><i class="fab fa-vuejs"></i><span>Vue</span> To Do List</h1>

    <div class="container">

      <div class="input">
            <input type="text" v-model="newItem" v-on:keyup.enter="addItem"/>
            <button class="add" v-on:click="addItem">+</button> <!-- @click for shorthand -->
      </div>

      <div class="todos">
        
          <ToDoItem v-for="todo in todos" :key="todo" :todo="todo" @delete="deleteItem" />
        
      </div>

    </div>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue'

export default {
  name: 'app',
  components: {
    ToDoItem
  },
  data(){
    return {
      todos: [],
      newItem: ""
    }
  },

  methods: {
    addItem(){
      if(this.newItem == ""){
        return;
      }

      this.todos.push(this.newItem);
      this.newItem = "";
    },

    deleteItem(todo){
      this.todos = this.todos.filter(item => item !== todo);
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro:300,700');

body{
  margin: 0;
  padding: 0;
  background: linear-gradient(to right, #11998e, #38ef7d);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: 'Source Sans Pro';
}

.todoList{
  text-align: center;
  border: 1px solid #00C387;
  background:#384660;
  width: 30vw;
  min-height: 70vH;
  height: auto;
  box-shadow: 2px 3px 15px rgba(0, 0, 0, 0.5);
  padding-bottom: 60px;
}

.header{
  color: #00C387;
  font-weight: 300;
  margin: 70px auto 30px;
}

i{
  margin-right: 10px;
}

span{
  font-family: 'Source Sans Pro';
  font-weight: 700;
}

.input{
  display: flex;
  justify-content: space-evenly;
  margin-bottom: 20px;
}

input{
  width: 60%;
  padding: 5px;
  font-size: 1em;
  box-shadow: 1px 3px 20px 0px rgba(0, 0, 0, 0.3);
  outline: none;
}

input:focus{
  border-color: #00C387;
}

button{
  outline: none;
}

.add{
  color: #00C387;
  font-size: 2em;
  width: 40px;
  height: 40px;
  padding: 0px;
  cursor: pointer;
  background: #384660;
  border-radius: 10px;
  box-shadow: 1px 1px 1px #399aba;
  border-color: #00C387;
}

.container{
  width: 80%;
  margin: 0 auto;
}

</style>
