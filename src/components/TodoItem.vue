<template>
    <li class="d-flex align-items-center list-group-item">
        <input type="text" class="flex-grow-1" v-model="msg" v-if="isEditing" @change="wasEdit(index)">
        <button v-else class="btn border-0 flex-grow-1 text-left" @click="checkTodo(index)"><span :class="complete ? 'done' : ''">{{ msg }}</span></button>
        <button class="btn btn-outline-primary border-0 ml-auto" @click="editTodo(index)"><i class="fas fa-edit"/></button>
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
            index: Number,
            isEditing: {
                type: Boolean,
                default: false
            }
        },
        methods: {
            checkTodo(index) {
                this.$emit("checkTodo", index);
            },
            removeTodo(index) {
                this.$emit("removeTodo", index);
            },
            editTodo(index) {
                this.$emit("editTodo", index);
            },
            wasEdit(index) {
                this.$emit("wasEdit", {index: index, msg: this.msg});
            }
        }
    }
</script>

<style scoped>
    .done {
        text-decoration: line-through;
    }
    .flex-grow-1 {
        flex-grow: 1;
    }
</style>