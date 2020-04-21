<template>
  <TodoList/>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
#app {
  margin: 0;
  padding: 0;
}
</style>
