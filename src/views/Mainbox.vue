<template>
  <div class="body">
    <div class="body_header">
        <Header />
    </div>

    <div class="body_container">
        <List :todos="todos"/>
    </div>

    <div class="body_footer">
        <Footer />
    </div>
  </div>
</template>

<script setup>
import {ref,reactive} from "vue"
import Footer from '@/components/Footer.vue'
import List from '@/components/List.vue'
import Header from '@/components/Header.vue'

let todos = reactive([
    {id:1,title:"吃饭",done:true},
    {id:2,title:"睡觉",done:true},
    {id:3,title:"打豆豆",done:true}
])
</script>

<style lang="scss" scoped>
.body{
    width: 500px;
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    align-items: center;
    .body_header{
        width: 100%;
        height: 50px;
        display: flex;
        justify-content: center;
        align-items: center;

    }
    .body_container{
        width: 92%;
        border-radius: 3px;

    }
    .body_footer{
        width: 92%;
        height: 40px;
        border-radius: 3px;
        border: 1px solid black;
        margin: 5px 0 10px 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        
    }
}

</style>
