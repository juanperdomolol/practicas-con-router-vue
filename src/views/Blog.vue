<template>
  <div>
      <Titulo texto="Titulo De Mi Blog"/>
      <!-- <button @click="consumirApi">Consumir API</button> -->
      <div v-for="item  in ArrayBlog" :key="item.id" > 
          <router-link :to="`/blog/${item.id}`">{{item.title}}</router-link>
            </div>
  </div>
</template>

<script>
import Titulo from "@/components/Titulo"
export default {
    components:{
        Titulo
    },
    data() {
    return {
        ArrayBlog: []
    }
},
methods: {
    async consumirApi(){
        try {
               const data = await fetch("https://jsonplaceholder.typicode.com/posts") 
               const array = await data.json()
               this.ArrayBlog = array
        } catch (error) {
            console.log(error)
        }
    }
},
created() {
    this.consumirApi()
},
}
</script>

<style>

</style>