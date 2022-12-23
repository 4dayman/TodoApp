<template>
  <div class="home">
    <nav>
      <router-link to="/about">About</router-link>
    </nav>
        <AddTodo @add-todo="addTodo" />
        <select v-model="filter">
          <option value="all">All</option>
          <option value="complited">Complited</option>
          <option value="not-complited">Not Complited</option>
        </select>
        <hr>
        <Loader v-if="loading"/>
        <TodoList v-else-if="filteredTodos.length" v-bind:todos="filteredTodos" @remove-todo="removeTodo" />
        <p v-else>No todos!</p>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'
export default {
  name: 'HomeView',
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },
  // watch: {
  //   filter(value) {
  //     console.log(value)
  //   }
  // },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      }
      if (this.filter === 'complited') {
        return this.todos.filter(t => t.completed)
      }
      if (this.filter === 'not-complited') {
        return this.todos.filter(t => !t.completed)
      }
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.todos = json
          this.loading = false
        }, 500)
      })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList, AddTodo, Loader
  }
}
</script>

<style scoped>
nav {
  padding: 10px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
