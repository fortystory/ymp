<script>
import { RouterLink, RouterView } from 'vue-router'

import { defineComponent } from 'vue'
import { keysStore } from './stores/keys'

// const keyboard = require('./src/config/keyborad.config');
// import { keyboard } from './config/keyborad.config'

// console.log(keyboard)
export default defineComponent({
  setup() {
    const keys = keysStore()
    return {
      keys
    }
  },
})

</script>

<template>
  <div class="basediv">
    <h1 class="green">逸码</h1>
    <nav>
      <RouterLink to="/">首页</RouterLink>
      <RouterLink to="/practice/">字根练习</RouterLink>
      <RouterLink to="/placeholder/跟打练习">跟打练习</RouterLink>
      <RouterLink to="/placeholder/字根浏览">字根浏览</RouterLink>
      <RouterLink to="/about">关于</RouterLink>
    </nav>
    <div></div><!-- 布局占位 -->
    <div></div><!-- 布局占位 -->
    <RouterView />
    <div></div><!-- 布局占位 -->
  </div>
</template>

<style scoped>

.basediv{
  display: grid;
  grid-template-columns: 1fr 10fr 1fr;
  grid-template-rows: 1fr 9fr;
}

nav {
  display:flex;
  font-size:2em;
  align-items: center; /* 垂直居中 */
  justify-content: center;/* 水平居中 */
}

nav a{
  margin-left: 5px;
  margin-right: 5px;
}

nav a.router-link-exact-active {
  color: var(--color-text);
  font-size:2em;
  margin-left: 30px;
  margin-right: 30px;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a:first-of-type {
  border: 0;
}

h1 {
  font-size: 4rem;
} 
</style>
