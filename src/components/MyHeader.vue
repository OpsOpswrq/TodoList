<template>
  <div>
<!--    <input type="text" placeholder="请输入你要做的事" v-model="item" @keyup.enter="addTodo">-->
    <input type="text" placeholder="请输入你要做的事" v-model="item">
    <button @click="addTodo">点我添加事务</button>
  </div>
</template>

<script>
export default {
  name: "MyHeader",
  data(){
    return {
      item:"",
      num:this.todos.length+1,
    }
  },
  props:['addTodoObj','todos'],
  methods:{
    addTodo(){
      if(this.item===null||this.item==='') return
      this.addTodoObj( new Object({
        id:this.num++,
        name:this.item,
        done:false
      }))
    }
  }
}
</script>

<style scoped>

</style>