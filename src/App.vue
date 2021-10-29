<template>

  <div class="wrapper">
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
  </div>
</template>

<script>
  import { ref } from 'vue';

  export default {
    setup() {

      const newTodo = ref('');
      const todos = ref([]);

      function addNewTodo() {
        if (newTodo.value === '') {
          alert('preencha o nome da tarefa')
          
        } else {
          todos.value.push({
            id: todos.value.length,
            estaCompleta: false,
            descricao: newTodo.value
          });
          newTodo.value = "";
        }
        
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
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    
    widows: 100%;
    display: flex;
    flex-direction: column;
  }

  #wrapper {
    width: 920px;
  }

  form {  
    display: flex;
    flex-direction: column;

    align-items: center;
    align-content: center;

  }

  input {
    height: 10px;
    width: 920px;
    font-size: 15px;
    padding: 5px;
  }  
  
  button {
    border: 0;
    width: 920px;
    padding: 0.6rem;
    border-radius: 0.3rem;
    font-size: 0.9rem;
    margin-top: 0.5rem;
    background-color: #17273f;
    color: white;
  }

  .todo {
    cursor: pointer;
  }

  .estaCompleta {
    text-decoration: line-through;
    color: red;
  }

</style>
