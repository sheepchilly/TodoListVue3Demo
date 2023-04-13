<template>
  <div class="filters">
    <span
      class="filter"
      :class="{active:selected === filter.value}"
      v-for="filter in arr"
      :key="filter.value"
      @click="$emit('change-filter', filter.value)"
      >{{ filter.label }}</span
    >
  </div>
</template>

<script>
export default {
  name: "TodoFilter",
  props:['selected'],
  setup() {
    const arr = [
      { label: "全部", value: "all" },
      { label: "已完成", value: "done" },
      { label: "未完成", value: "todo" },
    ];

    return {arr};
  },
};
</script>

<style>
.filters {
  display: flex;
  margin: 24px 2px;
  color: #c0c2ce;
  font-size: 14px;
}
.filters .filter {
  margin-right: 14px;
  transition: 0.8s;
  cursor: pointer;
}
.filters .filter.active {
  color: #6b729c;
  /* 放大1.2倍 */
  transform: scale(1.2);
}
</style>