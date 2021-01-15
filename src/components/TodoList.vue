<template>
    <div>
        <ul>
            <TodoItem 
            v-for="todo in todos" :key="todo.id"
            v-bind:todo="todo"
            @remove-todo="removeTodo"
            />
        </ul>
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
    props: ['todos'],
    components:  {
        TodoItem
    },
    methods: {
        removeTodo(id) {
            
            this.$emit('remove-todo', id);
        }
    }
}
</script>

<style scoped>
    ul {
        max-width: 50%;
        margin: 0;
        padding: 0;
        margin: 0 auto;
        list-style: none;
    }
</style>