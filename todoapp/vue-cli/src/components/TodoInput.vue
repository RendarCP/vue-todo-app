<template>
    <div>
      <input type="text" v-model="newTodoItem" placeholder="자신의 Todo 삽입" v-on:keyup.enter="addTodo">
      <button v-on:click="addTodo">추가</button>
    </div>
</template>

<script>
 export default{
    data(){
        return{
            newTodoItem:''
        }
    },
    methods:{
        addTodo(){
            if(this.newTodoItem !== ""){
                var value = this.newTodoItem && this.newTodoItem.trim();
                //localStorage.setItem(value,value);
                this.$emit('addTodo',value);
                this.clearInput();
            }
        },
        clearInput(){
            this.newTodoItem = '';
        }
    }
 }
</script>

<style>

</style>
