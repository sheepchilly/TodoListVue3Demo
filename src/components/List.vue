<template>
  <div>
    <Item />
  </div>
</template>

<script setup>
import { ref } from "vue"
import Item from '@/components/Item.vue'
</script>

<style lang="scss" scoped>
.container_list {
  height: 30px;
  line-height: 30px;
  border: 1px solid black;
  margin-bottom: 5px;
  position: relative;
  span{
            margin-left: 10px;
  }


}
</style>
