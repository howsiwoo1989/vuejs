<template>
  <div class="inputBox shadow">
      <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">

      <span class="addContainer" v-on:click="addTodo">
        <font-awesome-icon icon="fa-calendar-plus" />
          <i class="far fa-calendar-plus addBtn"></i>
      </span>

  </div>
</template>

<script>
export default {
    data: function(){
        return{
            newTodoItem: "",
        }
    },
    methods:{
        addTodo: function(){
            if(this.newTodoItem !==''){
                this.$emit('addTodoItem', this.newTodoItem);
                this.clearInput();
            }
        },        
        clearInput: function(){
            this.newTodoItem = '';
        }
    },
}
</script>

<style>
input:focus{
    outline: none;
}
.inputBox{
    background: #fff;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}
.inputBox input{
    height: 40px;

    width: 80%;

    border-style: none;

    font-size: 0.9rem;
}
.addContainer{
    float:right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
    overflow:hidden;
}
.addBtn{
  color: white;

        width: 50px;

        vertical-align: middle;
}
</style>