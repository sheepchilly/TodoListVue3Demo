<template>
  <div class="container_list">
    <label>
      <input type="checkbox" />
      <span>xx</span>
    </label>
    <button class="btn">删除</button>
  </div>
</template>

<script setup>
import { ref } from "vue"
</script>

<style lang="scss" scoped>
.btn {
  background: rgba(255, 0, 0, 0.644);
  border: none;
  color: white;
  width: 50px;
  height: 23px;
  text-align: center;
  border-radius: 5px;
  position: absolute;
  right: 10px;
  top: 3px;
  display: none;
}
</style>
