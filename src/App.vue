<template>
    <form @submit.prevent="addNewTodo">
      <label>Todo:</label>
      <input v-model="newTodo" name="newTodo">
      <button>Add new todo</button>
  </form>

  <ul>
    <li v-for="todo in todos" :key="todo.id" class="todo">
      <h3 :class="{ estaCompleta: todo.estaCompleta }" @click="toggleDone(todo)">
        {{todo.descricao}}
      </h3>
    </li>
  </ul>

</template>

<script>
import { ref } from 'vue';

export default {
  setup() {

    const newTodo = ref('');
    const todos = ref([]);

    function addNewTodo() {      
      todos.value.push({
        id: todos.value.length,
        estaCompleta: false,
        descricao: newTodo.value
      });
      newTodo.value = "";
    }

    function toggleDone(todo) {
      todo.estaCompleta = !todo.estaCompleta;
    }

    return {
      newTodo,
      addNewTodo,
      todos,
      toggleDone
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

.todo {
  cursor: pointer;
}

.estaCompleta {
  text-decoration: line-through;
}

</style>
