<template>
    <div id="app">
        <Header/>
        <AddTodo v-on:add-todo ="addTodo"/>
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
</template>

<script>
    import Header from './components/layout/Header';
    import Todos from './components/Todos';
    import AddTodo from './components/AddTodo';


    export default {
        name: "app",
        components: {
            Header,
            Todos,
            AddTodo
        },
        methods: {
            deleteTodo(id) {
                this.todos = this.todos.filter(todo => todo.id != id);
            },
            addTodo(newTodo){
                this.todos = [...this.todos,newTodo];
            }
        },
        data() {
            return {
                todos: [
                    {
                        id: 1,
                        title: "Todo One",
                        completed: false
                    }, {
                        id: 2,
                        title: "Todo Two",
                        completed: true
                    }, {
                        id: 3,
                        title: "Todo Three",
                        completed: false
                    },
                ]
            }
        }
    };
</script>

<style>
    /* reset */
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        font-family: Arial, Helvetica, sans-serif;
        line-height: 1.4;
    }
    .btn{
        display: inline-block;
        border: none;
        background: #555;
        color: #fff;
        padding: 7px 20px;
        cursor: pointer;
    }
</style>
