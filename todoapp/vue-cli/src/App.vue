<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItem" @removeTodo='removeTodo'></TodoList>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'

export default{
  data(){
   return{
     todoItem:[]
   }
  },
  methods:{
    addTodo(todoItem){
     	localStorage.setItem(todoItem, todoItem);
	    this.todoItems.push(todoItem);
    },
      removeTodo(todoItem,index){
        localStorage.removeItem(todoItem);
        this.todoItem.splice(index,1);
      }
  },
    created(){
       if(localStorage.length >0){
           for(var i=0; i <localStorage.length;i++){
               this.todoItems.push(localStorage.key(i));
           }
       }
   },
  components:{
    'TodoHeader': TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
  }
}
</script>

<style>
 body{
     text-align: center;
     background: #f6f6f8;
 }
 input{
     border-style: groove;
     width: 200px;
 }
 button{
     border-style: groove;
 }
 .shadow{
     box-shadow: 5px 10px 10px rgba(0,0,0,0.03)
 }
</style>
