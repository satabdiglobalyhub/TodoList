<template>
  <div class="container">
    <form @submit.prevent="addNewTodo">
      <label><h1>todos</h1> </label>
      <input
        type="text"
        name="newTodo"
        v-model="newTodo"
        placeholder="Enter Task"
        class="input"
        required
      />
      <button class="submit">Submit</button>
    </form>
    <button @click="markAllDone">Mark All Completed</button>
    <button @click="deleteAll">Delete All</button>
    <button @click="removeCompleted">Clear Completed</button>

    <ul>
      <li v-for="(todo, index) in todos" :key="todo.id" class="todo">
        <h3 :class="{ done: todo.done }" @dblclick="EditTodo(todo)">
          {{ todo.content }}
          <button @click="toggleDone(todo)">Completed</button>
          <button @click="removeTodo(index)">Delete</button>
        </h3>
      </li>
    </ul>

    <button @click="showAllTodo">All</button>
    <button @click="showActiveTodo">Active</button>
    <button @click="showCompletedTodo">Completed</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const newTodo = ref("");
    const todos = ref([]);

    function addNewTodo() {
      todos.value.push({
        id: Date.now(),
        done: false,
        content: newTodo.value,
      });
      newTodo.value = "";
      // console.log(todos);
    }

    function toggleDone(todo) {
      todo.done = !todo.done;
    }

    function removeTodo(index) {
      todos.value.splice(index, 1);
    }

    function markAllDone() {
      todos.value.forEach((todo) => {
        if (todo.done == false) {
          return (todo.done = !todo.done);
        }
      });
    }

    function deleteAll() {
      todos.value = [];
    }

    function removeCompleted() {
      for (let i = todos.value.length - 1; i >= 0; i--) {
        if (todos.value[i].done == true) {
          todos.value.splice(i, 1);
        }
      }
    }

    function showAllTodo() {
      todos.value.forEach((todo) => {
        console.log(todo.content);
      });
    }

    function showActiveTodo() {
      todos.value.forEach((todo) => {
        if (todo.done == false) {
          console.log(todo.content);
        }
      });
    }

    function showCompletedTodo() {
      todos.value.forEach((todo) => {
        if (todo.done == true) {
          console.log(todo.content);
        }
      });
    }

    return {
      newTodo,
      todos,
      addNewTodo,
      toggleDone,
      removeTodo,
      markAllDone,
      deleteAll,
      removeCompleted,
      showAllTodo,
      showActiveTodo,
      showCompletedTodo,
    };
  },
};
</script>

<style>
.container {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
.done {
  text-decoration: line-through;
}
form {
  margin-bottom: 20px;
}
.input {
  padding: 10px;
}
.submit {
  background: black;
  color: white;
  border-radius: 5px;
  padding: 10px;
}
</style>
