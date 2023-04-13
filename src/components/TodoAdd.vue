<template>
  <div class="input-add">
        <input type="text" name="todo" v-model="todoTitle" @keyup.enter="handleTodo"/>
        <button @click="handleTodo">
          <i class="plus"></i>
        </button>
      </div>
</template>

<script>
import {nanoid} from 'nanoid';
import {ref,reactive} from 'vue';
export default {
    name:'TodoAdd',
    props:['addTodo'],
    setup(props,context){
      let todoTitle = ref('')

      function handleTodo(){
        let todo = reactive({id:nanoid(),title:todoTitle.value,done:false})
        console.log(todo)
        context.emit('addTodo',todo)
        todoTitle.value = ''
      }

      return {
        todoTitle,
        handleTodo
      }
    }
}
</script>

<style>

</style>