<template>
    <li class="d-flex align-items-center list-group-item">
        <button class="btn border-0" @click="checkTodo(index)"><span :class="complete ? 'done' : ''">{{ msg }}</span></button>
        <button class="btn btn-outline-primary border-0 ml-auto" ><i class="fas fa-edit"/></button>
        <button class="btn btn-outline-danger border-0" @click="removeTodo(index)"><i class="fas fa-trash"/></button>
    </li>
</template>

<script>
    export default {
        name: "TodoItem",
        props: {
            id: {
                type: String
            },
            msg: {
                type: String,
                request: true
            },
            complete: {
                type: Boolean,
                default: false
            },
            index: Number
        },
        methods: {
            checkTodo(index) {
                this.$emit("checkTodo", index);
            },
            removeTodo(index) {
                this.$emit("removeTodo", index);
            }
        }
    }
</script>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>