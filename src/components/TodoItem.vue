<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <label>
            <input type="checkbox" @change="todo.completed = !todo.completed">
            <strong>{{ index + 1 }}</strong>
            {{ todo.title | uppercase }}
            </label>
        </span>
        <button class="remove" @click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        },
        index: Number
    },
    filters: {
        uppercase(value) {
            console.log(value)
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
    li {
        margin: 0;
        padding: 0;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
        display: flex;
        justify-content: space-between;
        border: 1px solid #ccc;
    }

    input {
        margin-right: 1rem;
    }

    .remove {
        background-color: firebrick;
        color: #ffffff;
        font-weight: bold;
        border-radius: 50%;
    }

    .done {
        text-decoration: line-through;
    }
</style>