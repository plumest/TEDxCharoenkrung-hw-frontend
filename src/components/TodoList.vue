<template>
    <div id="app">
        <div class="container">

            <div class="row">
                <div class="col-12 py-5">
                    <h1>My to-dos</h1>
                </div>
            </div>

            <div class="row mb-3">
                <form class="col-12 col-sm-10 col-md-8 col-lg-6" @submit.prevent="addTodo">
                    <input type="text" id="todo" placeholder="Create new to-do..." class="form-control" v-model="newTodo" required>
                </form>
            </div>

            <div class="row">
                <div class="col-12 col-sm-10 col-lg-6">
                    <ul class="list-group">
                        <TodoItem
                                v-for="(todo, index) in todos"
                                :key="todo.id"
                                :msg="todo.msg"
                                :id="todo.id"
                                :complete="todo.complete"
                                :index="index"
                                :isEditing="todo.isEditing"
                                @checkTodo="checkTodo"
                                @removeTodo="removeTodo"
                                @editTodo="editTodo"
                                @wasEdit="wasEdit"
                        />
                    </ul>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
    import TodoItem from "./TodoItem";
    import { uuid } from "vue-uuid";

    export default {
        name: "TodoList",
        components: {
            TodoItem
        },
        data () {
            return {
                newTodo: '',
                todos: []
            }
        },
        methods: {
            addTodo () {
                let todo = {
                    msg: this.newTodo,
                    id: uuid.v4(),
                    complete: false,
                    isEditing: false
                };
                this.todos.push(todo);
                this.newTodo = "";
            },
            checkTodo(index) {
                this.todos[index].complete = !this.todos[index].complete;
            },
            removeTodo(index) {
                this.todos.splice(index, 1);
            },
            editTodo(index) {
                this.todos[index].isEditing = !this.todos[index].isEditing;
            },
            wasEdit(todo) {
                let { index, msg } = todo;
                this.todos[index].msg = msg;
                this.todos[index].isEditing = false;
            }
        }
    }
</script>

<style scoped>

</style>