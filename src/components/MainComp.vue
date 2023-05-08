<script>
import CardComp from './CardComp.vue';
import { store } from '../store'



export default{
    name: "MainComp",
    components: { CardComp },
    data(){
      return{
        store
      }
    }
}

</script>

<template>
    <div class="w-75 bg-black d-flex align-items-center m-4">
        <h2 class="text-white">Numero Card: {{ store.arrayPersonaggi.length }}</h2>
    </div>
    <div class="d-flex flex-wrap justify-content-around">
        <CardComp/>
    </div>
</template>

<style lang="scss">
   div{
    height: 10%;
   }
</style>