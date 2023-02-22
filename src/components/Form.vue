<template>
  <div>
    <form @submit.prevent="addNewTodo" class="form">
      <input
        type="text"
        name="newTodo"
        v-model="newTodo"
        placeholder="What needs to be done?"
        class="todo-input"
        required
      />
      <button class="todo-submit">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: {},
    };
  },
  methods: {
    addNewTodo() {
      this.todos = {
        id: Date.now(),
        done: false,
        content: this.newTodo,
      };
      this.newTodo = "";
      this.saveData();
      this.$emit("updatedTodoList");
    },
    saveData() {
      let todosLists = JSON.parse(localStorage.getItem("todos")) || [];
      todosLists.push(this.todos);
      localStorage.setItem("todos", JSON.stringify(todosLists));
    },
  },
};
</script>

<style>
.form {
  display: flex;
  width: 100%;
  border: 3px solid #2c3e50;
}
.todo-input {
  width: 80%;
  padding: 10px 18px;
  font-size: 18px;
  border: none;
}
.todo-input:focus {
  outline: none;
}
.todo-submit {
  width: 20%;
  border-left: 3px solid #2c3e50;
  border-top: 0px;
  border-right: 0px;
  border-bottom: 0px;
  font-size: 20px;
  background-color: white;
}
.todo-submit:hover {
  color: white;
  background-color: black;
}
</style>
