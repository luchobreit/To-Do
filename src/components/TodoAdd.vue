<template>
    <form @submit="agregar" class="add-c">
        <input placeholder="Insertar" type="text" v-model="texto" >
    </form>
     
   
</template>


<script>
export default {
    data(){
        return{
            texto:""
        }
    },
    methods:{
        generacion(){
            const num=Math.random()*10000
            return num;
        },
        agregar(e){
            e.preventDefault();
            const n=this.generacion()
            const newtodo={ 
                id:n ,
                title:this.texto,
                completed:false
            };
            this.texto=""
            this.$emit('agregar', newtodo)
        }
    }
}
</script>

<style scoped>
 input{
     width: 70%;
     background-color: transparent;
     border: none;
     border-bottom: 2px solid tomato;
 }
 input:focus{
     outline: none;
 }
 input::placeholder{
     text-align: center;
 }

</style>