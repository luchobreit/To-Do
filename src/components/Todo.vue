<template>
    <div>
         <div class="todo" :key="todo.id" v-for="todo in todolist">
            <TodoItem :todo="todo" v-on:borrar="$emit('borrar',todo.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from "./TodoItem.vue"
export default({
    name: "Todo",
    props: ['todolist'],
    components:{TodoItem}
})
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Yuji+Hentaigana+Akari&display=swap');
    
    .todo{
        margin: 20px 0;
        padding: 5px 6px;
        text-align: initial;
        cursor: default;
        border-bottom: 1px solid black;
        max-height: 100%;
    }
    .todo:hover{
        background-color: #d6ecd3 ;
        box-shadow: 0px 10px 96px 38px rgba(145,199,136,1);
        
    }
</style>