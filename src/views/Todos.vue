<template>
  <div>
    <h2>Список дел</h2>
    <router-link to="/">Домой</router-link>
    <hr>
    <AddTodo 
    @add-todo="addTodo" />
    <hr>
    <Loader 
    v-if="loading"/>
    <TodoList v-else-if="todos.length"
    v-bind:todos="todos"
    @remove-todo="removeTodo" />
    <p v-else>Всё выполнено!</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'
export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
        this.loading = false
      })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(item => item.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo);
    }
  },
  components: {
   TodoList, AddTodo, Loader
  }
}
</script>