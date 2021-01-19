<template>
   <form @submit.prevent="onSubmit">
       <input type="text" v-model="title" required>
       <button type="submit">Добавить</button>
    </form> 
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            const newTodo = {
                id: Date.now(),
                title: this.title,
                comleted: false
            }
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        margin: 0 auto;
        max-width: 50%;
        display: flex;
    }

    input {
        width: 100%;
        font-size: 1.5rem;
    }
</style>