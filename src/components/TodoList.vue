<template>
  <div class="todo-list">
    <div v-for="(todo, index) in todos" :key="index" class="todo-item">
      <span class="todo-label">{{ todo.description }}</span>
      <Button
        icon="pi pi-pencil"
        class="p-button-roudend p-button-text"
        @click="$emit('editTodo', index)"
      />
      <Button
        icon="pi pi-trash"
        class="p-button-roudend p-button-text"
        @click="$emit('deleteTodo', index)"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todos: Array
  }
}
</script>

<style scoped>
  .todo-list {
    margin: 1rem;
  }

  .todo-item {
    display: flex;
    align-items: center;
    border-bottom: 1px solid lightgray;
  }

  .todo-label {
    flex-grow: 1;
  }
</style>