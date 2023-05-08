<script>
import {store} from "../store"
export default{
    name:"SearchPersonaggio",
    data(){
      return{
        store
      }
    }
    
}
</script>

<template>
    <select v-model="store.testoRicerca" name="" id="" class="my-3">
        <option v-for="(element, index) in store.arrayType" :value="element" class="text-center">{{ element }}</option>
    </select>
    <button type="button" class="btn btn-primary mb-2" @click="$emit('search')">Cerca</button>
</template>

<style lang="scss">
   
</style>