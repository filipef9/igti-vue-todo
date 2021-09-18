<template>
  <h1>Todo App</h1>

  <div v-if="!editMode">
    <Button @click="newTodo" >Novo</Button>
    <todo-list
      :todos="todos"
      @deleteTodo="deleteTodo"
      @editTodo="editTodo"
    />
  </div>

  <todo-item
    v-if="editMode"
    @voltar="voltar"
    @saveTodo="saveTodo"
    :todo="todo"
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
      todos: [],
      todo: null,
      nextId: 1
    }
  },
  methods: {
    newTodo() {
      this.todo = null;
      this.editMode = true;
    },
    voltar() {
      this.editMode = false;
    },
    saveTodo(todo) {
      if (todo.id) {
        const index = this.todos.findIndex(item => item.id === todo.id);
        this.todos[index] = { ...todo };
      } else {
        todo = { id: this.nextId, ...todo };
        this.todos = [...this.todos, todo];

        localStorage.setItem("nextId", ++this.nextId);
      }

      localStorage.setItem('todos', JSON.stringify(this.todos));
      this.editMode = false;
    },
    deleteTodo(indexTodoToDelete) {
      this.todos.splice(indexTodoToDelete, 1);
      localStorage.setItem('todos', JSON.stringify(this.todos));
    },
    editTodo(indexTodoToEdit) {
      this.todo = this.todos[indexTodoToEdit];
      console.log(this.todo);
      this.editMode = true;
    }
  },

  created() {
    const todos = localStorage.getItem("todos");
    if (todos) this.todos = [...JSON.parse(todos)];

    const nextId = localStorage.getItem('nextId');
    if (nextId) this.nextId = parseInt(nextId);
    else this.nextId = 1;
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
