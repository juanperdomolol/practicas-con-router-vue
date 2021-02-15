<template>
<div> 
    <Titulo texto="Articulo especifico" />
  <h2> Parámetro : {{$route.params.id}} </h2>
    <h3>{{articulo.title}}</h3>
    <hr>
    <p>{{articulo.body}}</p>
</div>
  
</template>

<script>
import Titulo from "@/components/Titulo"
export default {
    components:{
        Titulo 
    },
    data(){
        return{
            articulo: {}
        }
    },
    methods: {
        async consumirDatos(){
            try {
                // console.log(this.$route.params.id)
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                const objeto = await data.json()
                this.articulo = objeto
            } catch (error) {
                console.log(error)
            }
        }
    },
    created(){
        this.consumirDatos()
    }
}
</script>

<style>

</style>