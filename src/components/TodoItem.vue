<template>
    <li class="d-flex align-items-center list-group-item">
        <span>
            {{ msg }}
        </span>
        <button class="btn btn-outline-primary border-0" ><i class="fas fa-edit"/></button>
        <button class="btn btn-outline-danger border-0"><i class="fas fa-trash"/></button>
    </li>
</template>

<script>
    export default {
        name: "TodoItem",
        props: {
            msg: {
                type: String,
                request: true
            }
        }
    }
</script>

<style scoped>
</style>