<template>
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
</template>

<script>
export default {
  data() {
    return {
      todos: "",
      Newtodos: [],
    };
  },
  methods: {
    markAllDone() {
      const todos=JSON.parse((localStorage.getItem("todos")))
      if (!Array.isArray(todos)) {
    return;
      }
      todos.forEach(todo => {
        if (!todo.done) {
          todo.done = !todo.done;
        }
      });
      console.log(todos)
      localStorage.setItem("todos", JSON.stringify(todos));
      this.$emit("CompletedTodo");
    },

    clearCompleted() {
      for (let i = todos.value.length - 1; i >= 0; i--) {
        if (todos.value[i].done == true) {
          todos.value.splice(i, 1);
        }
      }
    },

    showAllTodo() {
      todos.value.forEach((todo) => {
        console.log(todo.content);
      });
    },

    showActiveTodo() {
      todos.value.forEach((todo) => {
        if (todo.done == false) {
          console.log(todo.content);
        }
      });
    },

    showCompletedTodo() {
      todos.value.forEach((todo) => {
        if (todo.done == true) {
          console.log(todo.content);
        }
      });
    }
  }
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
