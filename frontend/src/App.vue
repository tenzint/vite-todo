<script lang="ts">
import { ref, reactive } from "vue";

export default {
  setup() {
    const todoList = reactive([]);
    const newTodo = ref("");
    // list.value = []

    function appendList(newText: string) {
      if (newText === "") return;
      todoList.push({ name: newText });
      console.log("------------");
      console.log(todoList);
    }

    return { todoList, newTodo, appendList };
  },
};
</script>

<template>
  <input type="text" v-model="newTodo" />
  <button @click="newTodo = ''">Clear</button>
  <button @click="appendList(newTodo)">Add</button>
  <div>{{ todoList.length }}</div>
  <hr />
  <div>{{ newTodo }}</div>
  <hr />
  <div>{{ todoList }}</div>
  <hr />
  <ul>
    <li v-for="todo in todoList">{{ todo.name }}</li>
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
