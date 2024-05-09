<template>
  <div>
    <div class="h1">
      <h1><b>Daftar Tugas Anda</b></h1>
    </div>
    <input
      type="text"
      v-model="newTodo"
      @keyup.enter="addTodo"
      placeholder="Masukkan Tugas Anda..."
    />
    <ul>
      <li
        v-for="(todo, index) in todos"
        :key="index"
        @click="toggleCompleted(index)"
        :class="{ completed: todo.completed }"
      >
        {{ todo.text }}
        <button @click="removeTodo(index)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.push({ text: this.newTodo, completed: false });
        this.newTodo = "";
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
    toggleCompleted(index) {
      this.todos[index].completed = !this.todos[index].completed;
    },
  },
};
</script>

<style scoped>
body {
  font-family: "Roboto", sans-serif;
  font-style: bold;
  background-color: #f9fafb;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
#app {
  max-width: 400px;
  background-color: #0e014c;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
h1 {
  text-align: center;
  color: #ffffff;
}
input[type="text"] {
  width: calc(100% - 40px);
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin-bottom: 8px;
  padding: 10px;
  background-color: #f2f4f8;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.completed {
  text-decoration: line-through;
  color: #999;
}
button {
  padding: 6px 10px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
}
button:hover {
  background-color: #0056b3;
}
</style>
