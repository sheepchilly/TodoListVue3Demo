<template>
  <div class="todo-list">
        <todo-list-item :todos="item"  v-for="item in todos" :key="item.id"></todo-list-item>  
    </div>
</template>

<script>
import TodoListItem from './TodoListItem.vue';
export default {
    name:'TodoList',
    components:{TodoListItem},
    props:['todos']
}
</script>

<style>

</style>