<template>
  <h1>Todo App</h1>
  <div v-if="!editMode">
    <button @click="newTodo" >Novo</button>
    <todo-list></todo-list>
  </div>
  <todo-item v-if="editMode" @voltar="voltar"></todo-item>
</template>

<script>
import TodoList from './components/TodoList.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  components: {
    TodoList,
    TodoItem
  },
  data() {
    return {
      editMode: false
    }
  },
  methods: {
    newTodo() {
      this.editMode = true;
    },
    voltar() {
      this.editMode = false;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
