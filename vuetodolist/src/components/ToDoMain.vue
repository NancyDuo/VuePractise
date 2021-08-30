<template>
<!-- v-for is used in ul; send todo to li -->
  <ul class="todo-main" >
    <ToDoItem v-for= " li in todoList" 
              :key="li.id" 
              :todo="li"  
              :checkTodoValue = 'checkTodoValue' 
              :deleteTodo = 'deleteTodo' 
    />     
  </ul>
</template>

<script>
import ToDoItem from './ToDoItem.vue'
export default {
  name: 'ToDoMain',
  components:{ToDoItem},
  props:['todoList','checkTodoValue','deleteTodo']
  
}
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
