<template>
  <div class="form">
    <form @submit.prevent="addNewTodo">
      <input
        type="text"
        name="newTodo"
        v-model="newTodo"
        placeholder="What needs to be done?"
        class="todo-input"
        required
      />
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
      this.todos={
        id: Date.now(),
        done: false,
        content: this.newTodo,
      };
      this.newTodo = "";
      this.saveData();
      this.$emit("updatedTodoList");
    },
    saveData() {
      const todosLists = localStorage.getItem(
        "todos",
        JSON.stringify(this.todos)
      );
      console.log(todosLists);
      todosLists.push(this.todos);
      console.log(updatedTodos);
      localStorage.setItem("todos", JSON.stringify(updatedTodos));
    },
  },
};
</script>

<style>
.todo-input {
  width: 100%;
  padding: 10px 18px;
  font-size: 18px;
  margin-bottom: 16px;
  border: 2px solid #2c3e50;
}
</style>
