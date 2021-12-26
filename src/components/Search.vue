<template>
    <form @submit="reset" class="search-container">
        <input placeholder="Buscar" v-model="querry" @input="$emit('filtrar',querry)" type="text" >
    </form>
</template>

<script>
export default {
    name:"Search",
    data(){
        return{
            querry:''
        }
    },
    methods:{
        reset(e){
            e.preventDefault();
            this.querry=""
        }
    }
}
</script>

<style scoped>

input{
    width: 500px;
    height: 25px;
    background-color: transparent;
    border: none;
    border-bottom: 2px solid tomato;
    color: white;
    font-size: 20px;
    
}
input::placeholder{
    text-align: center;
}
input:focus{
    outline: none;
    
}

</style>