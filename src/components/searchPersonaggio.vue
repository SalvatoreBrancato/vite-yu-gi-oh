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
    <select v-model="store.testoRicerca" name="" id="" class="mb-2">
        <option v-for="(element, index) in store.arrayType" :value="element">{{ element }}</option>
    </select>
    <button type="button" class="btn btn-primary mb-2" @click="$emit('search')">Cerca</button>
</template>

<style lang="scss">
   
</style>