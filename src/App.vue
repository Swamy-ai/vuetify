<template>
  <v-app>
    <Header v-on:add-todo="addTodo"/>
    <TodoAll v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </v-app>
</template> 

<script>
import Header from './components/Header.vue'
import TodoAll from './components/TodoAll.vue'
export default {
  name: 'App',
  components: {
    Header,
    TodoAll
  },
  data(){
    return{
      todos:[]
    }
  },
  methods:{
    deleteTodo(id){
      let url="https://jsonplaceholder.typicode.com/todos/"+id;
                let options = {
            method: "DELETE",
            headers: {
              "Content-Type": "application/json",
              Accept: "application/json",
            }
          };
          fetch(url, options)
            .then(function(response) {
              return response.json();
            })
      this.todos = this.todos.filter(todo => todo.id !==id)
    },
    addTodo(newTodo){
      let data = {
              title:newTodo.title,
              completed:newTodo.completed
              };
      let options = {
                method: "POST",
                headers: {
                  "Content-Type": "application/json",
                  Accept: "application/json",
                },
                body: JSON.stringify(data)
              };
      fetch("https://jsonplaceholder.typicode.com/todos", options)
                .then(function(response) {
                  return response.json();
                })
                    this.todos = [...this.todos,newTodo];
                  }
                },
  created(){
    let options={
      methods:"GET",
    }
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=10",options)
    .then(response =>response.json())
    .then(jsondata =>this.todos=jsondata)
    .catch(err=>console.log(err));
  }
  
}
</script>
