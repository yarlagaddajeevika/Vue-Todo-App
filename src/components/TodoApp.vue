<!-- TodoApp.vue -->
<template>
  <div>
    <h1>Vue.js Todo App</h1>
    
    <div>
      <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new todo">
      <button @click="addTodo">Add</button>
    </div>

    <ul>
      <TodoItem v-for="(todo, index) in todos" :key="index" :todo="todo" @remove="removeTodo(index)" />
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push(this.newTodo.trim());
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  },
  components: {
    TodoItem
  }
};
</script>
