<script>
    let id = 0

    export default{
        data(){
            return{
                newTodo: "",
                todoList: [

                ]
            }
        },
        methods:{
            addTodo(){
                this.todoList.push( {id: id++, text: this.newTodo});
                this.newTodo = ""
            },
            removeTodo(todo){
                this.todoList.splice(todo, 1);
            }
        },
        watch:{
            todoList() {
                console.log(this.todoList);
            }
        }
    }
</script>

<template>
    <div class="container">
        <h2 class="app-name">Todo List</h2>
        <form @submit.prevent="addTodo">
            <input v-model="newTodo">
            <button class="add-button">Add Todo</button>
        </form>
        <ul>
            <li class="todo-item" v-for="todo in todoList" :key="todo.id">
                {{todo.text}}
                <button @click="removeTodo(todo)">X</button>
            </li>
        </ul>
    </div>

</template>

