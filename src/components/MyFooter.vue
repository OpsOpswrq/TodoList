<template>
  <div>
    <input type="checkbox" v-bind:checked="totalChecked" @change="checkAll(!totalChecked)">
    <span>已完成:{{number}}/事情总数:{{todos.length}}</span>
    <button @click="removeAllChecked">删除已完成的事情</button>
  </div>
</template>

<script>
export default {
  name: "MyFooter",
  props:['todos','checkTodoList','number','removeAllChecked','checkAllTodo'],
  computed:{
    totalChecked(){
      return this.number === this.todos.length&&this.todos.length>0
    },
  },
  methods:{
    checkAll(checked){
      this.checkAllTodo(checked)
    }
  }
}
</script>

<style scoped>

</style>