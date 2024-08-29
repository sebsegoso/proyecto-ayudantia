<template>
  <form @submit.prevent="enviarTarea">
    <label for="addTask">Agregar tarea</label>
    <input id="addTask" type="text" placeholder="Ingresa una tarea..." v-model="nuevaTarea" />
    <button type="submit">Agregar tarea</button>
  </form>
</template>

<script>
export default {
  name: 'CreateToDoForm',
  data() {
    return {
      nuevaTarea: ''
    }
  },
  methods: {
    enviarTarea() {
      if (!this.nuevaTarea.trim()) return

      this.$emit('submit-tarea', this.nuevaTarea.trim())
      this.nuevaTarea = ''
    }
  }
}
</script>

<style scoped>
form {
  padding: 2rem;
  display: flex;
  gap: 0.5rem;
}
</style>