<template>
    <li class="d-flex align-items-center list-group-item">
        <button class="btn border-0">{{ msg }}</button>
        <button class="btn btn-outline-primary border-0 ml-auto" ><i class="fas fa-edit"/></button>
        <button class="btn btn-outline-danger border-0"><i class="fas fa-trash"/></button>
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
            }
        }
    }
</script>

<style scoped>
</style>