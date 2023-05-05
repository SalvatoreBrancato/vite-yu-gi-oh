<script>
import {store} from '../store'

export default{
    name:"CardComp",
    data(){
      return{
        store
      }
    }
    
}
</script>

<template>
    <div v-for="(element, index) in store.arrayPersonaggi" class="card mb-2" style="width: 18rem;">
        <img :src="element.card_images[0].image_url" class="card-img-top" alt="immagine personaggio">
        <div class="card-body">
            <h5 class="card-title">{{element.name}}</h5>
            <p class="card-text">{{element.type}}</p>
        </div>
    </div>
</template>

<style lang="scss">
   
</style>