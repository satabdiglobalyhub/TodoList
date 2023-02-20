<template>
  <button @click="markAllDone">Mark All Completed</button>
  <button @click="deleteAll">Delete All</button>
  <button @click="removeCompleted">Clear Completed</button>
  <button @click="showAllTodo">Show All</button>
  <button @click="showActiveTodo">All Active</button>
  <button @click="showCompletedTodo">All Completed</button>
</template>

<script>
export default {
  setup() {
    function markAllDone() {
      todos.value.forEach((todo) => {
        if (todo.done == false) {
          return (todo.done = !todo.done);
        }
      });
    }

    function deleteAll() {
      localStorage.clear();
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

<style></style>
