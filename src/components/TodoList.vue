<template>
  <div class="todo-list">
        <todo-list-item v-for="n in 3" :key="n"></todo-list-item>  
    </div>
</template>

<script>
import TodoListItem from './TodoListItem.vue';
export default {
    name:'TodoList',
    components:{TodoListItem}
}
</script>

<style>

</style>