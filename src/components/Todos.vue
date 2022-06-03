<template>
  <div
    class="transition-all duration-500 bg-zinc-800 w-full h-screen flex justify-center items-center flex-col"
  >
    <h1 class="font-bold text-7xl text-green-200">Todo App</h1>
    <div
      class="input my-12 w-full px-14 lg:px-56 flex flex-wrap sticky top-0 left-0 z-10"
    >
      <input
        class="w-full lg:w-4/5 py-3 px-8 rounded-lg outline-none border-green-600 border-2 hover:border-green-300"
        type="text"
        placeholder="Type a Todo . . ."
        v-model="newTodo"
      />
      <button
        class="w-full lg:w-1/5 cursor-pointer bg-green-500 text-white font-bold py-3 px-8 rounded-lg"
        @click="addTodo()"
      >
        Add Todo
      </button>
    </div>
    <!-- Todo's Container -->
    <ul class="w-full px-14 lg:px-56">
      <!-- Todos -->
      <li
        class="bg-green-50 rounded-2xl w-full py-4 pl-6 pr-9 my-4 font-bold text-xl relative"
        v-for="(index, Todo) in Todos"
        :key="Todo.id"
      >
        {{ Todo }} - {{ index }}
        <!-- Close Icon -->
        <box-icon
          name="x-circle"
          color="white"
          class="bg-red-500 absolute right-3 top-4 rounded-full cursor-pointer"
          @click="removeTodo(index)"
        ></box-icon>
      </li>
    </ul>
  </div>
</template>

<script>
// Import BoxIcons
import "boxicons";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Todos",
  data() {
    return {
      newTodo: "",
      Todos: [
        "Build a Todo App wiht Angular",
        "Build a Todo App with Vue.js",
        "Build a Todo App with React",
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo == "") {
        alert("Input is Empty");
      } else {
        this.Todos.push(this.newTodo);
        this.newTodo = "";
      }
    },
    removeTodo(index) {
      this.Todos.splice(index, 1);
    },
  },
};
</script>
