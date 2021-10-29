<template>
    <form @submit.prevent="addNewTodo">
      <label>Todo:</label>
      <input v-model="newTodo" name="newTodo">
      <button>Add new todo</button>
  </form>

</template>

<script>
import { ref } from 'vue';

export default {
  setup() {

    const newTodo = ref('');

    function addNewTodo() {
      console.log(newTodo.value)
    }

    return {
      newTodo,
      addNewTodo,
    }
  }
}
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
