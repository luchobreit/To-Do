<template>
    <div class="todo-body" >
        <div class="todo-body" :class="{completed: todo.completed}">
            <input type="checkbox"
                :checked= 'todo.completed ? "checked" : "" ' 
                v-on:change="checkTodo">
           <label>{{todo.title}}</label>
        </div>

        <div class="todo-action">
            <button @click="$emit('borrar', todo.id)">Eliminar</button>
        </div>
    </div>
</template>

<script>
    export default {
        name:'TodoItem',
        props:{
            todo: Object,
        },
        methods:{
            checkTodo(){
                this.todo.completed= !this.todo.completed
            }
        }
    }
</script>

<style scoped>
.completed{
    text-decoration: line-through;
    color: grey;
}
.todo-body{
    width: 100%;
    display: flex;
    align-items: center;
    margin-left: 2px;
}
.todo-action{
  margin-right: 10%;
}
input{
    cursor: pointer;
    border-radius: 20px;
    height: 20px;
}
label{
    margin-left: 20px;
}
button{
    cursor: pointer;
    height: 30px;
    background: transparent;
    border: none;
    border-bottom: 2px solid orangered;
    border-radius: 2px;
    position: relative;
}
button:hover{
    outline: none;
    background-color: brown;
     border-bottom: 4px solid black;
}
.item-c{
    display: flex;
}

</style>