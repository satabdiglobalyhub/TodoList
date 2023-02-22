<template>
  <div class="list">
    <div v-if="todosList.length">
      <div v-for="(todo, index) in todosList" :key="index" class="todo">
        <h3 :class="{ done: todo.done }">
          <input
            type="checkbox"
            @click="todoCompleted(todo)"
            :checked="todo.done"
          />
          <label @dblclick="editTodo(todo)" :class="{ completed: todo.done }">
            {{ todo.content }}
          </label>
          <button

            @click="deleteTodo(index)"
            class="button-delete"
          >
            Delete
          </button>
        </h3>
      </div>
      <div class="deleteAll">
        <button v-if="todosList.length > 1" @click="deleteAllTodo()" class="button-deleteAll">
          Delete All
        </button>
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
    todoCompleted(todo) {
      todo.done = !todo.done;
      localStorage.setItem("todos", JSON.stringify(this.todosList));
    },
    deleteTodo(index) {
      this.todosList.splice(index, 1);
      localStorage.setItem("todos", JSON.stringify(this.todosList));
    },
    editTodo(todo) {
      const newContent = prompt("Enter new content", todo.content);
      if (newContent !== null && newContent !== "") {
        todo.content = newContent;
        localStorage.setItem("todos", JSON.stringify(this.todosList));
      }
    },
    deleteAllTodo() {
      localStorage.clear();
      this.todosList.splice(0, this.todosList.length);
      this.$emit("deletedtodosList", this.todosList);
    },
  },
};
</script>

<style>
.list {
  padding: 10px;
  border-bottom: 3px solid #2c3e50;
}
input {
  margin-right: 10px;
}
.completed {
  color: #2c3e50;
  text-decoration: line-through;
}
.deleteAll {
  display: flex;
  justify-content: end;
}
.button-delete,
.button-deleteAll {
  font-size: 20px;
  border: 1px solid black;
  border-radius: 5px;
  background-color: white;
  margin-left: 20px;
}

.button-delete:hover,
.button-deleteAll:hover {
  color: white;
  background-color: black;
}
</style>
