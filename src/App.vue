<template>
  <h1>Todo App</h1>

  <div v-if="!editMode">
    <Button @click="newTodo" >Novo</Button>
    <todo-list :todos="todos"></todo-list>
  </div>

  <todo-item
    v-if="editMode"
    @voltar="voltar"
    @saveTodo="saveTodo"
  ></todo-item>
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
      editMode: false,
      todos: []
    }
  },
  methods: {
    newTodo() {
      this.editMode = true;
    },
    voltar() {
      this.editMode = false;
    },
    saveTodo(todo) {
      this.todos = [...this.todos, todo];
      localStorage.setItem('todos', JSON.stringify(this.todos));
      this.editMode = false;
    }
  },

  created() {
    const todos = localStorage.getItem("todos");
    if (todos) {
      this.todos = [...JSON.parse(todos)];
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
