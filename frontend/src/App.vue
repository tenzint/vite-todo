<script lang="ts">
import { ref, reactive, defineComponent } from "vue";

export default defineComponent({
  setup() {
    const todoList = reactive([]);
    const newTodo = ref("");
    // list.value = []

    function appendList(newText: string) {
      if (newText === "") return;
      todoList.push({ name: newText });
    }

    function removeTodo(entry) {
      const index = todoList.indexOf(entry, 0);
      if (index > -1) {
        todoList.splice(index, 1);
      }
    }

    return { todoList, newTodo, appendList, removeTodo };
  },
});
</script>

<template>
  <input type="text" v-model="newTodo" />
  <button @click="newTodo = ''">Clear</button>
  <button @click="appendList(newTodo)">Add</button>
  <ul>
    <li v-for="(todo, i) in todoList" :key="todo.id">
      {{ todo.name }}<button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
