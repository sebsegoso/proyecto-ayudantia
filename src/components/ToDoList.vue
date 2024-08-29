<template>
  <ul v-if="listaTareas.length > 0">
    <li
      :style="{
        textDecoration: tarea.isDone ? 'line-through' : 'none'
      }"
      :class="['list-item', { 'list-item--done': tarea.isDone }]"
      v-for="tarea in listaTareas"
      :key="tarea.id"
    >
      <input type="checkbox" @change="marcarTareaHecha(tarea.id)" />
      {{ tarea.title }}

      <button @click="$emit('elimina-tarea', tarea.id)">X</button>
    </li>
  </ul>
  <p v-else>No hay tareas agregadas, debes agregar una tarea</p>
</template>

<script>
export default {
  name: 'ToDoList',
  props: {
    listaTareas: Array
  },
  methods: {
    marcarTareaHecha(id) {
      this.$emit('marcar-como-hecha', id)
    }
  }
}
</script>

<style>
.list-item {
  border: 1px solid black;
  padding: 0.25rem 0.5rem;
}
.list-item--done {
  opacity: 0.5;
}
</style>