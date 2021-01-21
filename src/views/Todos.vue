<template>
  <div>
    <h2>Список дел</h2>
    <router-link to="/">Домой</router-link>
    <hr>
    <AddTodo 
    @add-todo="addTodo" />
    <select v-model="filter">
        <option value="all">Все</option>
        <option value="completed">Выполненые</option>
        <option value="not-completed">Не выполненые</option>
    </select>
    <hr>
    <Loader 
    v-if="loading"/>
    <TodoList v-else-if="filteredTodo.length"
    v-bind:todos="filteredTodo"
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
      loading: true,
      filter: "all"
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
  computed: {
      // eslint-disable-next-line vue/return-in-computed-property
      filteredTodo() {
        if (this.filter === "all") {
              return this.todos
        }
        if (this.filter === 'completed') {
            return this.todos.filter(t => t.completed)
        }
        if (this.filter === 'not-completed') {
            return this.todos.filter(t => !t.completed)
        }
      }
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