<template>
    <div id="app">
        <Header/>
        <AddTodo v-on:add-todo="addTodo"/>

        <Todos v-bind:todos="todos" v-on:del-todo="delTodo"/>

    </div>
</template>

<script>
    import Header from "@/components/layout/Header";
    import Todos from "@/components/Todos";
    import AddTodo from "@/components/AddTodo";

    export default {
        name: 'App',
        components: {Header, Todos, AddTodo},
        methods: {
            delTodo(id) {
                this.todos = this.todos.filter(todo => todo.id !== id)
            },
            addTodo(title) {
                const newTodo = {
                    id: Math.max.apply(Math, this.todos.map(function(t) { return t.id; })) + 1,
                    title: title,
                    completed: false
                };
                console.log(newTodo);
                this.todos = [...this.todos, newTodo]
            }
        },
        data() {
            return {
                todos: [
                    {
                        id: 1,
                        title: "Todo One",
                        completed: false
                    },
                    {
                        id: 2,
                        title: "Todo Two",
                        completed: true
                    },
                    {
                        id: 3,
                        title: "Todo Three",
                        completed: false
                    }
                ]
            }
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        font-family: Arial, Helvetica, sans-serif;
        line-height: 1.4;
    }

    .btn {
        display: inline-block;
        border: none;
        background: #555;
        color: #fff;
        padding: 7px 20px;
        cursor: pointer;
    }

    .btn:hover {
        background: #666;
    }
</style>
