<template>
    <div class="footer_left">
        <input type="checkbox" />
        <span>已完成 0 / 全部 2 </span>
    </div>
    <div class="footer_right">
        <button class="btn">清除已完成任务</button>
    </div>
</template>

<script setup>
import { ref } from "vue"
</script>

<style lang="scss" scoped>
.footer_right {
    margin-right: 10px;

    .btn {
        background: rgba(255, 0, 0, 0.644);
        color: white;
        border: none;
        border-radius: 4px;
        padding: 4px;
    }
}
</style>
