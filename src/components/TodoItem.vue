<template>
    <li>
        <span>
            <input type="checkbox">
            <strong>{{ todo.id }}</strong>
            {{ todo.title }}
        </span>
        <button class="remove">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
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