<template>
  <div id="app">
    <section class="todoapp">
      <header class="header">
        <h1 class="title">todos</h1>
        <input class="new-todo"
          autofocus autocomplete="off"
          placeholder="What needs to be done?"
          v-model="newTodo"
           @keyup.enter="addTodo">
      </header>
      <section class="main">
        <input class="toggle-all" type="checkbox">
        <ul class="todo-list">
          <li class="todo"
             v-for="(todo, key) in todos"
              :key="key">
            <div class="view">
              <label>{{ todo }}</label>
              <button class="destroy" @click="removeTodo(todo)"></button>
            </div>
          </li>
        </ul>
      </section>
    </section>
    <footer class="footer">
      <button @click="removeAllTodos" class="clear-completed">
        Remove all
      </button>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      todos: [],
      newTodo: ''
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo !== '') {
        this.todos.push(this.newTodo);
        this.newTodo = '';
      }
    },
    removeTodo(todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
    },
    removeAllTodos() {
      this.todos = [];
    }
  }
};
</script>

<style lang="css" src="../public/styles.css">
</style>
