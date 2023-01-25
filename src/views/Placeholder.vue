<!-- 占位符 -->
<script>
export default {
  props: ['message']
}
</script>
<template>
    <div class="item">{{ $route.params.message }}</div>
</template>

<style scoped>
.item {
  font-size:3rem;
  margin-top: 2rem;
  display: flex;
}
</style>
