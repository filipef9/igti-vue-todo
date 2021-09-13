<template>
  <div v-for="(todo, index) in todos" :key="index">
    <span>{{ todo.description }}</span>
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

</style>