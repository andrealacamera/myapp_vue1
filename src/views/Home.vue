<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
//import teiga from './components/HelloWorld.vue'
import Todos from '../components/Todos'
import AddTodo from '../components/AddTodo'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    Todos, 
    AddTodo
  },
  data() {
    return {
      todos: [
      // {
      //   id: 1,
      //   title: 'Imparare Vue.js',
      //   completed: false
      // },
      // {
      //   id: 2,
      //   title: 'Inserire Vue.js in WordPress',
      //   completed: false
      // },
      // {
      //   id: 3,
      //   title: 'Creare WebApp LibrInCasa',
      //   completed: false
      // }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      //axios DELETE request
      //returns promise
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => {
        console.log(res.status);
        //qui occorrerebbe controllare se lo status e' 200 (OK) per proseguire e cancellare per davvero...
        return this.todos=this.todos.filter(todo => todo.id!==id);
        
      })
      .catch(err => console.log(err));


      //this.todos = this.todos.filter(todo => todo.id !== id)
      //arrow function per tenere tutti i todo che non sono quello cancellato
    },
    addTodo(newTodo){
      //use spread operator, to copy old todos and add the new one.
      //this.todos = [...this.todos, newTodo]

      //extract title and completed from newTodo
      const {title, completed} = newTodo
      //axios POST request
      //returns promise
      const newLocal='https://jsonplaceholder.typicode.com/todos'

      axios.post(newLocal, {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));
    }
  },
  created() {
    const newLocal='https://jsonplaceholder.typicode.com/todos?_limit=7'
    //axios GET request 
    //returns a promise
    axios.get(newLocal)
    .then(res => this.todos = res.data)
    .catch(err => console.log("errore axios",err));
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin:0;
  padding:0;
}
body {
  font-family: Ubuntu, 'Helvetica Neue';
  /* text-align: center; */
  /* color: red; */
  /* margin-top: 20px; */
}
.btn {
  display: inline-block;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
