<template>
  <div>
    <div class="buttons-complete">
      <button @click="markAllDone">Mark All Completed</button>
      <button @click="removeCompleted" class="buttons-complete--clear">
        Clear Completed
      </button>
    </div>
    <div class="buttons-show">
      <button @click="showAllTodo">All</button>
      <button @click="showActiveTodo">Active</button>
      <button @click="showCompletedTodo">Completed</button>
    </div>
  </div>
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

<style>
.buttons-complete {
  padding: 10px;
  display: flex;
  justify-content: space-between;
  color: black;
}
.buttons-complete button {
  font-size: 20px;
  border: 1px solid black;
  border-radius: 5px;
  background-color: white;
}
.buttons-show {
  padding: 10px;
  display: flex;
  justify-content: flex-start;
}
.buttons-show button {
  margin-right: 10px;
  font-size: 20px;
  border: 1px solid black;
  border-radius: 5px;
  background-color: white;
}

.buttons-complete button:hover,
.buttons-show button:hover {
  color: white;
  background-color: black;
}
</style>
