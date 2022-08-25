<template>
  <div id="wrap">
    <todo-header></todo-header>
    <todo-input v-on:addTodoItem="addOneItem"></todo-input>
    <todo-list v-bind:propsdata="todoItems" v-on:removeItem="removeOneItem"></todo-list>
    <todo-footer></todo-footer>
  </div>
</template>

<script>

import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'


export default {
  data: function(){
    return{
      todoItems: []
    }
  },
  methods:{
    addOneItem : function(todoItem){
      var obj = {completed: false, item: todoItem};
      //로컬스토리지 저장
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todoItems.push(obj);
    },
    removeOneItem : function(item, idx){
      localStorage.removeItem(item.item);
      this.todoItems.splice(idx, 1);
    },
  }
  ,
  created: function(){
    if(localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++){
        this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
      }
    }
  },
  components:{
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter,
  },
}
</script>

<style>
body{
  text-align: center;
  background-color: #f6f6f6;
}
input{
  border-style:groove;
  width: 200px;
}
button{
  border-style: groove;
}
.shadow{
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
