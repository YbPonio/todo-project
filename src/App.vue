<template>
    <TodoHeader />
    <RouterView />
</template>

<script setup>
import TodoHeader from './components/TodoHeader.vue';
import { RouterView } from 'vue-router';
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Martian+Mono:wght@100;200;300;400;500;600;700;800&family=Roboto:wght@100;300;400;500;700;900&display=swap');
* {
  font-family: 'Martian Mono', monospace;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

</style>