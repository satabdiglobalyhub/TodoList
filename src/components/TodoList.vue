<template>
  <div class="list">
    <ul v-if="todosList.length">
      <li v-for="(todo, index) in todosList" :key="index" class="todo">
        <h3 :class="{ done: todo.done }" @dblclick="editTodo(todo)">
          {{ todo.content }}
          <button @click="todoCompleted(todo)">Completed</button>
          <button @click="removeTodo(index)">Delete</button>
        </h3>
      </li>
    </ul>
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
    todoCompleted(todo) {
      todo.done = !todo.done;
    },
    removeTodo(index) {},
    editTodo(todo) {
      const newContent = prompt("Enter new content", todo.content);
      if (newContent !== null && newContent !== "") {
        todo.content = newContent;
      }
    },
  },
  computed: {},
};
</script>

<style>
.list {
  padding: 10px;
  border-bottom: 2px solid #2c3e50;
}
</style>
