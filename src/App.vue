<template>

<div class="app" id="app">
    <div class="header" id="header">
      <Search v-on:filtrar="filtro"/>
    </div>

    <div class="todo-container" id="main-container">

      <h2 class="titulo">Tareas</h2>

      <TodoAdd v-on:agregar="agregarItem"/>

      <Todo :todolist="copytodos" v-on:borrar="borrarItem"/>

    </div>
  </div>
</template>

<script>
import Search from './components/Search'
import TodoAdd from './components/TodoAdd'
import Todo from "./components/Todo.vue"

export default {
  name: 'App',
  components: {
    Search,
    TodoAdd,
    Todo
  },
  methods: {
    borrarItem(id){
      this.todos=this.todos.filter(r=>r.id !== id);
      this.copytodos=[...this.todos]
    },
    agregarItem(item){
      this.todos.push(item)
      this.copytodos=[...this.todos]
    },
    filtro(query){
      const text= query.toUpperCase()
      if (text.trim()==="") {
        this.copytodos=[...this.todos];
      }else{
        const temp =this.todos.filter(r=>{
          return r.title.includes(query)
        });

        this.copytodos=[...temp]
      }
    }
  },
  data(){
    return{
      todos: [
        {
          id: 0,
          title:  'comprar la cena',
          completed: false
        },
        {
         id: 1,
         title: 'Sacar a pasear al perro',
         completed: true
       },
       {
         id: 2,
         title: 'jugar Xbox',
         completed: false
       },
       {
         id: 3,
         title: 'Terminar tutorial',
         completed: true
       }
      ],
      copytodos: []
    }
  },
  created(){
    this.copytodos = [...this.todos];
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@300&display=swap');
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  
}
body{
  font-family: 'Comfortaa', cursive;
  font-weight: bolder;
}
.app{
  width: 100%;
  height: 100%;
  min-height: 100vh;
  display: flex;
  justify-items: center;
  align-items: center;
  background-color: #A6CF98;
  flex-flow: column;
}
.todo-container{
        border: 5px double black;
        text-align: center;
        background: #91C788;
        width: 60%;
        height: fit-content;
        margin-top: 5%;
}
  
.titulo{
        font-size: 35px;
        padding-bottom: 20px;
        font-family: 'Yuji Hentaigana Akari', cursive;
}

.header{
  width: 100%;
  height: 40px;
  background-color: #2E4C6D;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
