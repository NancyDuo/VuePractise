<template>
  <div class="todo-footer" v-show = 'total'>
    <label>
      <input type="checkbox" :checked = 'checkAll' @change="toCheckAll"/>
      
    </label>
    <span>
        <span> Completed: {{doneNum}}</span> / Total: {{total}}
    </span>
    <button class="btn btn-danger" @click= "deleteDone" >Clear All Completed</button>
  </div>
</template>

<script>


export default {
  name: 'ToDoFooter',
  props:["todoList" , 'checkedAll' , 'deleteAllDone'],
  computed : {
    total(){
      return this.todoList.length
    },
    doneNum(){
      return this.todoList.reduce( (pre,cur) => pre + (cur.isDone ? 1 : 0),0 )
     
    },
    checkAll(){
      return (this.total === this.doneNum) && (this.total >0)
    },
      
    
  },
  methods: {
    toCheckAll(e){
      this.checkedAll(e.target.checked)
      

    },
    deleteDone(){
      this.deleteAllDone()
    }
  },
  
}
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}

</style>
