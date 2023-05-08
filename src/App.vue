<script>
import MainComp from './components/MainComp.vue';
import NavComp from './components/NavComp.vue';
import { store } from './store';
import axios from 'axios';
import SearchPersonaggio from './components/searchPersonaggio.vue';
import Spinner from './components/Spinner.vue'

export default{
  name: "App",
  components:{
    NavComp,
    MainComp,
    SearchPersonaggio,
    Spinner
},
data(){
  return{
    store
  }
},
computed:{
  chiamataApi(){
    store.spinner = true
    if(store.testoRicerca == ''){
      axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=1`)
      .then( (res) =>{
        const dataApi = res.data.data
  
        this.store.arrayPersonaggi = dataApi
        store.spinner = false
        for (let i = 0; i < dataApi.length; i++) {
          const dataApiType = res.data.data[i].type
          //console.log(dataApiType)
          if(!store.arrayType.includes(dataApiType) ){
            store.arrayType.push(dataApiType)
          }
        }
      })
    }  else{
      axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=1&type=${store.testoRicerca}`)
      .then( (res) =>{  
        const dataApi = res.data.data
  
        this.store.arrayPersonaggi = dataApi
        store.spinner = false

        for (let i = 0; i < dataApi.length; i++) {
          const dataApiType = res.data.data[i].type
          //console.log(dataApiType)
          if(!store.arrayType.includes(dataApiType) ){
            store.arrayType.push(dataApiType)
          }
        }
      })
    }   
  }
}
}
</script>

<template>
  <NavComp/>
<div class="sfondo">
  <div class="box d-flex align-items-center flex-column my-5 ">
    <SearchPersonaggio @search="chiamataApi"/>
    <Spinner v-if="store.spinner"/>
    <MainComp/>
  </div>
</div>
</template>

<style lang="scss">
@use "./style/main.scss";

.sfondo{
  background-color: rgb(251, 187, 11);
  display: flex;
  justify-content: center;
  align-items: center;
  .box{
    background-color: white;
    height: 80%;
    width: 80%;
  }
}
</style>
