<template>
  <div class="todo-header">
    <input type="text" placeholder="type in your memo and press enter" @keydown.enter="addTodo"/>
  </div>
</template>

<script>
import {nanoid} from 'nanoid'

export default {
  name: 'ToDoHeader',
  // receive function from app
  props:['addList'],
  methods: {
    addTodo(event){
      if(!event.target.value.trim()) return
      //receive new todolist
      const todoObj = {
        id:nanoid(), memo:event.target.value, isDone:false
      }
      this.addList(todoObj)
      event.target.value = ''
    }
  },
 
}
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}


</style>
