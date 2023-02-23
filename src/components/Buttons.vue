<template>
  <div v-if="todosList.length > 1">
    <div>
      <div class="buttons-complete">
        <button @click="markAllDone">Mark All Completed</button>
        <button @click="clearCompleted">Clear Completed</button>
      </div>
      <div class="buttons-show">
        <button @click="showAllTodo">All</button>
        <button @click="showActiveTodo">Active</button>
        <button @click="showCompletedTodo">Completed</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todosList: Array,
  },
  data() {
    return {
      todos: "",
      Newtodos: [],
    };
  },
  methods: {
    markAllDone() {
      const todos = JSON.parse(localStorage.getItem("todos"));
      const allDone = todos.every((todos) => todos.done);
      todos.forEach((todos) => {
        todos.done = !allDone;
      });
      localStorage.setItem("todos", JSON.stringify(todos));
      this.$emit("CompletedTodo");
    },

    clearCompleted() {
      const todos = JSON.parse(localStorage.getItem("todos"));
      for (let i = todos.length - 1; i >= 0; i--) {
        if (todos[i].done == true) {
          todos.splice(i, 1);
        }
      }
      localStorage.setItem("todos", JSON.stringify(todos));
      this.$emit("CompletedTodo");
    },

    showAllTodo() {
      const todos = JSON.parse(localStorage.getItem("todos"));
    },

    showActiveTodo() {
      const todos = JSON.parse(localStorage.getItem("todos"));
      todos.forEach((todos) => {
        if (todos.done == false) {
          todos = todos.content;
        }
      });
      
    },

    showCompletedTodo() {
      const todos = JSON.parse(localStorage.getItem("todos"));
      todos.forEach((todos) => {
        if (todos.done == true) {
          console.log("completed-", todos.content);
        }
      });
    },
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
