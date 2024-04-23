<script>
import { ref } from "vue";

export default {
  setup() {
    const nombreLista = ref ("Mi lista de quehaceres")
    const todos = ref ([{nombre: "Quehacer 1"}, {nombre: "Quehacer 2"}, {nombre: "Quegacer 3"}])
    const nuevoTodo = ref("")

    const agregarTodo = () => {
      if (nuevoTodo.value.trim()) {
        todos.value.push({ nombre: nuevoTodo.value})
        nuevoTodo.value = ""
        
      }
    }

    const eliminarTodo = (index) => {
      todos.value.splice(index, 1)
    }
    return {nombreLista, todos, nuevoTodo, agregarTodo, eliminarTodo}
  }
}
</script>

<template>
  <div id="app">
    <h1>Lista de Quehaceres</h1>
    <input v-model="nombreLista" placeholder="Nombre de su lista de quehaceres" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input v-model="todo.name">
        <button @click="eliminarTodo(index)">Eliminar</button>

      </li>
    </ul>
    <input v-model="nuevoTodo" placeholder="Nuevo quehacer">
    <button @click="agregarTodo()">Agregar quehacer</button>
    
  </div>
</template>

<style scoped>

</style>
