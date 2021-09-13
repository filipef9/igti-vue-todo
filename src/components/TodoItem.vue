<template>
  <InputText v-model="description" />
  <Button @click="voltar">Voltar</Button>
  <Button @click="saveTodo">Salvar</Button>
</template>

<script>
export default {
  data() {
    return {
      description: ''
    }
  },
  methods: {
    voltar() {
      this.$emit('voltar');
    },
    saveTodo() {
      this.$emit('saveTodo', { description: this.description });
    }
  }
}
</script>

<style scoped>

</style>
