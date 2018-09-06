<template>
  <div class="item">
    <p class="todo">{{todo}}</p>
    <button class="delete" v-on:click="deleteItem(todo)">-</button>
  </div>
</template>

<script>
export default {
  name: 'ToDoItem',
  props: ['todo'],
  methods: {
    deleteItem(todo){
      this.$emit('delete', todo)
    }
  }
}
</script>

<style>
.item{
  display: flex;
  align-items: center;
}

.todo{
  background: #47597a;
  color: white;
  width: 90%;
  padding: 15px;
  margin-right: 20px;
}

.delete{
  width: 35px;
  height: 35px;
  cursor: pointer;
  background: #384660;
  border-radius: 10px;
  border-color: #ff6961;
  color: #ff6961;
  font-size: 18px;
}
</style>


