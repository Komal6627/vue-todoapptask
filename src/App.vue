<template>
  <div id="app">
    <!-- <TodoApp /> -->
    <AdTodo />
  </div>
</template>

<script>
import TodoApp from './components/TodoApp.vue';
import AdTodo from './components/AdTodo.vue';

export default {
  name: 'App',
  components: {
    AdTodo,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
