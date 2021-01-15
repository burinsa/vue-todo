<template>
  <div id="app">
    <h1>Список дел</h1>
    <AddTodo />
    <hr>
    <TodoList v-bind:todos="todos"
    @remove-todo="removeTodo" />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/Addtodo'
export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'Свалить из страны', comleted: false},
        {id: 2, title: 'Войти в IT', comleted: false},
        {id: 3, title: 'Покормить кошек', comleted: false}
      ]
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(item => item.id !== id)
    }
  },
  components: {
   TodoList, AddTodo
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
