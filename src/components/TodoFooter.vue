<template>
  <div>
      <span v-on:click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods:{
    clearTodo: function(){
      localStorage.clear();
    },
  }
}
</script>

<style>

</style>