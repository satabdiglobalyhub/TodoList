<template>
  <div>
    <button @click="logtodo">logtodo</button>
  </div>
  <ul>
    <!-- <li v-for="(todo, index) in todo" :key="todo.id" class="todo">
      <h3 :class="{ done: todo.done }" @dblclick="editTodo(todo)">
        {{ todo.content }}
        <button @click="toggleDone(todo)">Completed</button>
        <button @click="removeTodo(index)">Delete</button>
      </h3>
    </li> -->
  </ul>
</template>

<script>
export default {
  setup() {
    let todos = "";
    let Newtodos = [];
    todos = localStorage.getItem("todos");
    const obj = JSON.parse(todos);
    const length = Object.keys(obj).length;
    function logtodo() {
      console.log(obj);
      console.log(length);
    }
    // function toggleDone(todo) {
    //   todo.done = !todo.done;
    // }

    // function removeTodo(index) {
    //   todo.value.splice(index, 1);
    // }

    // function editTodo(todo) {
    //   const newContent = prompt("Enter new content", todo.content);
    //   if (newContent !== null && newContent !== "") {
    //     todo.content = newContent;
    //   }
    // }

    return {
      todos,
      Newtodos,
      logtodo,
      // toggleDone,
      // removeTodo,
      // editTodo,
    };
  },
};
</script>

<style></style>
