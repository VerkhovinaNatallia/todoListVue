<template>
  <div id="app" class="app">
    <img src="./image/To-Do-List-floral.jpg">

    <TodoList />
  </div>
</template>

<script setup lang="ts">
import TodoList from './components/TodoList.vue';
</script>

<style scoped>
img{
    width: 100%;
  }
  .app{
    width: 700px;
    margin: 0 auto;;
  }
</style>