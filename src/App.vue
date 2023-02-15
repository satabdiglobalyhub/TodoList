<template>
  <form @submit.prevent="addNewTodo">
    <label>todos</label>
    <input
      type="text"
      name="newTodo"
      v-model="newTodo"
      placeholder="Enter Task"
      required
    />
    <button>Submit</button>
  </form>
  <button @click="markAllDone">Mark All done</button>
  <button @click="deleteAll">Clear All</button>
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
      console.log(todos);
      newTodo.value = "";
    }

    function toggleDone(todo) {
      todo.done = !todo.done;
    }

    function removeTodo(index) {
      todos.value.splice(index, 1);
    }

    function markAllDone() {
      todos.value.forEach((todo) => (todo.done = !todo.done));
    }

    function deleteAll() {
      todos.value = [];
    }
    function removeCompleted() {}

    function showAllTodo() {}

    function showActiveTodo() {}

    function showCompletedTodo() {}
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
.todo {
  cursor: pointer;
}
.done {
  text-decoration: line-through;
}
</style>
