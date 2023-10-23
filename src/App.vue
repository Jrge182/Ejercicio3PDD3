<template>
  <div>
    <h2>Contador</h2>
    <p>El valor del contador es: {{ count }}</p>
    <button @click="increment">Incrementar</button>
    <button @click="decrement">Decrementar</button>
  </div>

  <div>
    <h2>To-Do List</h2>
    <input v-model="newTodo" placeholder="Ingresa una tarea">
    <button @click="addTodo">Añadir</button>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        <input type="checkbox" v-model="todo.completed">
        {{ todo.text }}
        <button @click="removeTodo(todo)">Remove</button>
      </li>
    </ul>
  </div>

</template>

<script>
export default {
  name: 'Counter',
  data() {
    return {
      count: 0,
      todos: [],
      newTodo: '',
    };
  },
  methods: {
    increment() {
      this.count++;
    },
    decrement() {
      this.count--;
    },

    addTodo() {
      if (this.newTodo) {
        this.todos.push({
          id: Date.now(),
          text: this.newTodo,
          completed: false,
        });
        this.newTodo = '';
      }
    },
    removeTodo(todo) {
      this.todos = this.todos.filter(t => t.id !== todo.id);
    },
  },
};



</script>