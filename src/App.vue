<template>
  <main>
    <div class="container">
      <h1>欢迎使用 sheep 待办事项</h1>
      <todo-add @addTodo="addTodo" :tid="todos.length"/>
      <todo-filter :selected="filter" @change-filter="filter = $event"/>
      <todo-list :todos="filteredTodos"/>
    </div>
  </main>
</template>

<script>
import {reactive,provide,ref,watch,nextTick,computed} from 'vue';
import TodoAdd from "./components/TodoAdd.vue";
import TodoFilter from "./components/TodoFilter.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    TodoAdd,
    TodoFilter,
    TodoList,
  },
  setup(props,context){
    //这样读取空数组会报错，试一下vuex存
    let todos = reactive([
      // JSON.parse(localStorage.getItem('todos')) 

      // {id:'001',title:'吃饭',done:false},
      // {id:'002',title:'睡觉',done:true},
      // {id:'003',title:'打豆豆',done:true}
  ]) 
    // watch(todos,()=>{
    //   nextTick(()=>{
    //   console.log('我存储了信息')
    //   localStorage.setItem('todos',JSON.stringify(todos))
    // })
    // },{deep:true})

    const filter = ref('all');
    const filteredTodos = computed(()=>{
      switch(filter.value){
        case "done":
          return todos.filter(todo=>todo.done);
        case "todo":
          return todos.filter(todo=>!todo.done)
        default:
          return todos
      }
    })

    function handleCheck(todo){
        reactive(todos.filter(item=>{
          return item.id === todo.id
        }))
    }
    provide('handleCheck',handleCheck)

    function addTodo(newTodo){
      todos.unshift(newTodo)
    }

    return{
      todos,
      handleCheck,
      addTodo,
      filter,
      filteredTodos
    }
  }

};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Helvetica, sans-serif, "microsoft Yahei";
}
main {
  width: 100vw; /* 占满整个屏幕 */
  min-height: 100vh; /* 如果有很多个todo的话可能会把页面撑开，
  形成滚动条。设置min-height的话整个背景容器会一直向下到滚动条最底部，如果设置成height的话他就只会在第一屏有背景色（滚动条没滚动）
  当向下滚动的时候下面就会变成白色的 */
  display: grid;
  align-items: center;
  justify-items: center;
  background: rgb(203, 210, 240);
}
.container {
  width: 60%;
  max-width: 400px; /* 最大宽度 */
  box-shadow: 0px 0px 24px rgba(0, 0, 0, 0.15);
  border-radius: 24px;
  padding: 48px 28px;
  background: rgb(245, 246, 252);
}
h1 {
  margin: 24px 0;
  font-size: 28px;
  color: #414873;
}
/* 输入框 */
.input-add {
  position: relative;
  display: flex;
  align-items: center;
}
.input-add input {
  /* 把输入框撑开 */
  padding: 16px 52px 16px 18px;
  border-radius: 48px;
  border: none;
  /* 去掉外边线 */
  outline: none;
  box-shadow: 0px 0px 24px rgba(0, 0, 0, 0.08);
  width: 100%;
  font-size: 16px;
  color: #626262;
}
.input-add button {
  width: 46px;
  height: 46px;
  border-radius: 50%;
  /* linear-gradient 生成渐变 */
  background: linear-gradient(#c0a5f3, #7f95f7);
  /* 去掉边框和外边线 */
  border: none;
  outline: none;
  color: white;
  /* 绝对定位 */
  position: absolute;
  right: 0px;
  cursor: pointer;
}
.input-add .plus {
  display: block; /* 块级元素让他宽高占满整个按钮 */
  width: 100%;
  height: 100%;
  /* 设置按钮的加号 */
  background: linear-gradient(#fff, #fff), linear-gradient(#fff, #fff); /* 生成加号->一个横着的线和一个竖着的线 */
  background-size: 50% 2px, 2px 50%;
  background-position: center;
  /* 设置成不平铺，剩下的50%的空间就不会显示背景了 */
  background-repeat: no-repeat;
}

.todo-list {
  /* 设置成grid布局方便设置每一个todoItem的间距 */
  display: grid;
  row-gap: 14px;
}
.todo-item {
  background: white;
  padding: 16px;
  border-radius: 8px;
  color: #626262;
}
.todo-item label {
  position: relative;
  display: flex;
  align-items: center;
}
.todo-item label span.check-button {
  position: absolute;
  top: 0;
}
/* before是空心圆，after是实心圆 */
.todo-item label span.check-button::before,
.todo-item label span.check-button::after {
  content: "";
  display: block;
  position: absolute;
  width: 18px;
  height: 18px;
  border-radius: 50%;
}
.todo-item label span.check-button::before {
  border: 1px solid #b382f9;
}
.todo-item label span.check-button::after {
  /* 设置0.4秒的过渡时间 */
  transition: 0.4s;
  background: #b382f9;
  /* 缩小成0.8倍，向下移动1px */
  transform: translate(1px, 1px) scale(0.8);
  opacity: 0;
}
.todo-item input {
  margin-right: 16px;
  opacity: 0;
}
.todo-item input:checked + span.check-button::after {
  opacity: 1;
}
</style>
