<template>
  <div class="container">
    <h1 class="title">todos</h1>
    <Form @updatedTodoList="updatedTodoList" />
    <TodoList :todosList="todosList" @deletedtodosList="todosList" />
    <Buttons :todosList="todosList" />
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import Buttons from "./components/Buttons.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    Form,
    Buttons,
    TodoList,
  },
  data() {
    return {
      todosList: [],
    };
  },
  mounted() {
    this.logtodo();
  },
  methods: {
    logtodo() {
      const savedTodos = localStorage.getItem("todos");
      if (savedTodos) {
        this.todosList = JSON.parse(savedTodos);
      }
    },
    updatedTodoList() {
      this.logtodo();
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: Arial, Helvetica, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 24px;
}
.container {
  max-width: 600px;
  margin: 0 auto;
}
.title {
  margin-top: 50px;
  display: flex;
  justify-content: center;
}
</style>
