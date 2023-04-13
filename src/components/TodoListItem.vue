<template>
  <div class="todo-item" :class="{done:todos.done}">
            <label>
              <input type="checkbox" @change="changeCheck(todos)" :checked="todos.done"/>
              {{ todos.title }}
              <span class="check-button"></span>
            </label>
          </div>
</template>

<script>
import {ref,reactive,inject} from 'vue';
export default {
    name:'TodoListItem',
    props:['todos'],
    setup(props,context){
      const handleCheck = inject('handleCheck');
      const changeCheck = (todo)=>{
        todo.done = !todo.done;
        console.log(todo.done)
        handleCheck(todo);
      }
      return {
        changeCheck
      }
    }
}
</script>

<style>
.todo-item.done label{
  text-decoration: line-through;  /* 添加删除线 */
  font-style: italic; /* 设置斜体 */
}
</style>