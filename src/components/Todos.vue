<template>
    <button @click="fetchTodos">Fetch Todos</button>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
            <h2 v-if="todo.completed == true">
                Título: {{todo.title}} <br/>
                Completed: {{todo.completed}}
            </h2>
        </li>
    </ul>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Todos',
        data() {
            return {
                todos: [],
                baseURI: "https://jsonplaceholder.typicode.com/todos"
        }; 
    },
    methods:{
        fetchTodos: function(){
            axios.get(this.baseURI).then((result) => {
                this.todos = (result.data);
            });
        } 

    },
};
</script>

<style>

</style>