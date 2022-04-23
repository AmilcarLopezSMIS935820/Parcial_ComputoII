<template>
    <div style="border: 1pt solid #fbb; text-align: center;">
        <table  align="center">
            <tr>
                <th>ID</th><br/>  <br/><th>Nombre</th><br/>  <br/><th>Genero</th><br/> <th>Categoria</th> <br/>
            </tr>
                <tr v-for="todo in todos" :key="todo.id">
                    <td>{{todo.id}}</td><br>
                    <td>{{todo.nombre}}</td><br>
                    <td>{{todo.genero}}</td><br>
                    <td>{{todo.categoria}}</td><br>
                </tr>

        </table>
    </div>
</template>

<script>

    import axios from 'axios'
    export default{
        data(){
           return {todos: null}
        },
        mounted(){
            this.getTodos();
        },
        methods:{
            getTodos(){
                axios.get('http://127.0.0.1:8000/api/multimedia/').then(response=>{
                    this.todos = response.data
                }).catch(e =>console.log(e))
            }
        }

    }
</script>

<style>
</style>

