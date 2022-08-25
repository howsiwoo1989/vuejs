<template>
  <div>
      <ul>
        <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
          <i class="fas fa-check"  v-bind:class="{checkBtnCompleted : todoItem.completed}" v-on:click="toggleComp(todoItem, index)"></i>
          {{ todoItem.item }}
          <span v-bind:class="{textCompleted : todoItem.completed}" v-on:click="removeTodo(todoItem, index)">
            <i class="fas fa-trash-alt"></i>
          </span>
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  props: ['propsdata'],
  methods:{
    removeTodo: function(item, idx){
      this.$emit('removeItem', item, idx);
    },
    // toggleComp:function(item, idx){
    //   item.completed = !item.completed;
    //   localStorage.removeItem(item.item);
    //   localStorage.setItem(item.item, JSON.stringify(item))
    // },
  },

}
</script>

<style>

</style>