<template>
  <p>Todo Item</p>
  <button @click="voltar">Voltar</button>
</template>

<script>
export default {
  methods: {
    voltar() {
      this.$emit('voltar');
    }
  }
}
</script>

<style scoped>

</style>
