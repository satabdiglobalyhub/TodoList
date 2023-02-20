<template>
  <div>
    <button @click="logtodo">logtodo</button>
  </div>
  <ul v-if="Newtodos.length">
    <li v-for="(todo, index) in Newtodos" :key="index" class="todo">
      <h3 :class="{ done: todo.done }" @dblclick="editTodo(todo)">
        {{ todo.content }}
        <button @click="toggleDone(todo)">Completed</button>
        <button @click="removeTodo(index)">Delete</button>
      </h3>
    </li>
  </ul>
</template>

<script>
export default {
  setup() {
    let todos = "";
    let Newtodos = [];

    function logtodo() {
      todos = localStorage.getItem("todos");
      const obj = JSON.parse(todos);
      let list = [];
      for (let i = 0; i < obj.length; i++) {
        console.log(obj[i].content);
        list.push(obj[i].content);
      }
      return list;

      const length = Object.keys(obj).length;
      console.log(length);
    }

    function toggleDone(todo) {
      todo.done = !todo.done;
    }

    function removeTodo(index) {
      Newtodos.splice(index, 1);
    }

    function editTodo(todo) {
      const newContent = prompt("Enter new content", todo.content);
      if (newContent !== null && newContent !== "") {
        todo.content = newContent;
      }
    }

    return {
      todos,
      Newtodos,
      logtodo,
      toggleDone,
      removeTodo,
      editTodo,
    };
  },
};
</script>

<style></style>
