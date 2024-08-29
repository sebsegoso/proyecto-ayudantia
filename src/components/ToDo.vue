<template>
  <div>
    <!-- formulario -->
    <CreateToDoForm @submit-tarea="agregarTarea" />
    <!-- lista de tareas -->
    <ToDoList
      :listaTareas="tareas"
      @elimina-tarea="eliminarTarea"
      @marcar-como-hecha="marcarTareaComoHecha"
    />
  </div>
</template>

<script>
import CreateToDoForm from './CreateToDoForm.vue'
import ToDoList from './ToDoList.vue'

export default {
  name: 'ToDo',
  components: { CreateToDoForm, ToDoList },
  data() {
    return {
      tareas: []
    }
  },
  methods: {
    agregarTarea(textoTarea) {
      const nuevaTarea = { id: new Date().getTime(), title: textoTarea, isDone: false }

      this.tareas.push(nuevaTarea)
    },
    eliminarTarea(id) {
      this.tareas = this.tareas.filter((tarea) => tarea.id !== id)
    },
    marcarTareaComoHecha(id) {
      this.tareas = this.tareas.map((tarea) => {
        if (tarea.id === id) {
          return { ...tarea, isDone: !tarea.isDone }
        }
        return tarea
      })
    }
  }
}
</script>

<style>
</style>