<template>
  <div>
    <table>
      <thead>
      <td>是否完成</td>
      <td>事情</td>
      <td>操作</td>
      </thead>
      <tbody>
      <tr v-for="item in todos" v-bind:key="item.id">
        <td><input type="checkbox" v-bind:checked="item.done" @change="checkDone(item.id)"></td>
        <td><span>{{item.name}}</span></td>
        <td><button @click="removeTodoObj(item.id)">删除</button></td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "MyList",
  props:['todos','removeTodo','checkTodo'],
  methods:{
    removeTodoObj(id){
      this.removeTodo(id)
    },
    checkDone(id){
      this.checkTodo(id)
    }
  }
}
</script>

<style scoped>

</style>