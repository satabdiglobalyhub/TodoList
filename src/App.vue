<template>
  <div class="container">
    <Form />
    <TodoList />
    <Buttons />
  </div>
</template>

<script>
import { ref, defineComponent } from "vue";
import Form from "./components/Form.vue";
import Buttons from "./components/Buttons.vue";
import TodoList from "./components/TodoList.vue";

export default defineComponent({
  components: {
    Form,
    Buttons,
    TodoList,
  },
});
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
