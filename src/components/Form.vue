<template>
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
  <div></div>
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
      saveData();
    }
    function saveData() {
      localStorage.setItem("todos", JSON.stringify(todos.value));
    }

    return {
      newTodo,
      todos,
      addNewTodo,
    };
  },
};
</script>
