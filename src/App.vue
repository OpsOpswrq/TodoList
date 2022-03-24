<template>
  <div>
    <MyHeader :addTodoObj="addTodoObj" :todos="todos"/>
    <MyList :todos="todos" :removeTodo="removeTodo" :checkTodo="checkTodo"/>
    <MyFooter :todos="todos" :number="totalNum" :removeAllChecked="removeAllChecked" :checkAllTodo="checkAllTodo"/>
  </div>
</template>

<script>
import MyHeader from "@/components/MyHeader";
import MyList from "@/components/MyList";
import MyFooter from "@/components/MyFooter";
export default {
  data(){
    return {
      todos:[
        {id:1,name:'吃饭',done:false},
        {id:2,name:'编程',done:true},
        {id:3,name:'睡觉',done:false}
      ],
      totalNum:0
    }
  },
  components:{MyHeader,MyList,MyFooter},
  methods:{
    addTodoObj(todoObj){
      this.todos.unshift(todoObj)
    },
    removeTodo(id){
      this.todos = this.todos.filter((todoObj)=>{
        return todoObj.id !== id
      })
      this.checkTodoList()
    },
    checkTodoList(){
      this.totalNum = this.todos.reduce((pre,todo)=>{
        return pre+todo.done
      },0)
    },
    checkTodo(id) {
      this.todos.forEach((todoObj)=>{
        if(todoObj.id === id){
          todoObj.done = !todoObj.done
        }
      })
      this.checkTodoList()
    },
    removeAllChecked(){
      this.todos = this.todos.filter((todo)=>{
        return !todo.done
      })
      this.checkTodoList()
    },
    checkAllTodo(checked){
      this.todos.forEach((todo)=>{
        todo.done = checked
      })
      this.checkTodoList()
    }
  },
  mounted() {
    this.totalNum = this.todos.reduce((pre,todo)=>{
      return pre+todo.done
    },0)
  }
}
</script>

<style scoped>

</style>