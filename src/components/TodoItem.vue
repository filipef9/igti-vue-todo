<template>
  <InputText v-model="description" />
  <div class="mt-1">
    <Button @click="voltar" class="mr-1">Voltar</Button>
    <Button @click="saveTodo">Salvar</Button>
  </div>
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
  .mt-1 {
    margin-top: 1rem;
  }

  .mr-1 {
    margin-right: 1rem;
  }
</style>
