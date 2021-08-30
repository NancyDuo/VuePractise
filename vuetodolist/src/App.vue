<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <!-- send function to header; use this function to receive data -->
        <h1>Todo List</h1>
        <ToDoHeader :addList = 'addList' />
        <ToDoMain :todoList= "todoList" :checkTodoValue = 'checkTodoValue' :deleteTodo = 'deleteTodo' />
        <ToDoFooter :todoList= "todoList" :checkedAll = 'checkedAll' :deleteAllDone = 'deleteAllDone' />
      </div>
    </div>
  </div>
</template>

<script>
import ToDoHeader from './components/ToDoHeader.vue'
import ToDoMain from './components/ToDoMain.vue'
import ToDoFooter from './components/ToDoFooter.vue'


export default {
  name: 'App',
  //setup all elements
  components: {ToDoHeader,ToDoMain,ToDoFooter},
  //save data
  data() {
    return {
      todoList:[
        {id:'01',memo:'Drinking',isDone:true},
        {id:'02',memo:'Eating',isDone:false}]
        
    }
  },
  
  //receive input list value
  methods: {
    addList(todoObj){
      this.todoList.unshift(todoObj)

    },
    checkTodoValue(idVal){
      this.todoList.forEach( ele => {
        if(idVal === ele.id){
          ele.isDone = !ele.isDone
        }
      })
    },
    deleteTodo(idVal){
      this.todoList = this.todoList.filter(element => element.id !== idVal)  
    
    },
    checkedAll(val){
      this.todoList.forEach(element => {
        element.isDone = val
      });
    },
    deleteAllDone(){
      this.todoList = this.todoList.filter(element => element.isDone === false)  
    }
    
  },
  watch: {
			todoList:{
				deep:true,
				handler(value){
					localStorage.setItem('todoList',JSON.stringify(value))
				}
			}
		},
  

}
</script>

<style scoped>

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
 
}
</style>
