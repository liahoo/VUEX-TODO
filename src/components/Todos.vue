<template>
 <div>
  <h3>Todos</h3>
  <div class="todos">
   <div
    v-for="todo in allTodos"
    :key="todo.id"
    @click="toggleTodo(todo)"
    class="todo"
    v-bind:class="{'is-completed': todo.completed}"
   >
    {{todo.id}}. {{todo.title}}
    <i @click="deleteTodo(todo.id)" class="fas fa-trash-alt"></i>
   </div>
  </div>
 </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
 name: "Todos",
 methods: {
  ...mapActions(["fetchTodos", "deleteTodo", "updateTodo", "toggleTodo"])
 },
 computed: mapGetters(["allTodos"]),
 created() {
  this.fetchTodos();
 }
};
</script>

<style scoped>
.todos {
 display: grid;
 grid-template-columns: repeat(3, 1fr);
 grid-gap: 1rem;
}
.todo {
 border: 1px solid #ccc;
 background: #8fea12;
 padding: 1rem;
 border-radius: 5px;
 position: relative;
 text-align: center;
 cursor: pointer;
}
i {
 position: absolute;
 bottom: 10px;
 right: 10px;
 color: #fff;
 cursor: pointer;
}
.is-completed {
  background: #ccc;
  color: #eee;
}
</style>