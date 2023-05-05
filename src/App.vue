<script>
import MainComp from './components/MainComp.vue';
import NavComp from './components/NavComp.vue';
import { store } from './store';
import axios from 'axios';

export default{
  name: "App",
  components:{
    NavComp,
    MainComp
},
data(){
  return{
    store
  }
},
created(){
  this.chiamataApi()
},
methods:{
  chiamataApi(){
    axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=1')
    .then( (res) =>{
      console.log(res.data.data)

      const dataApi = res.data.data

      this.store.arrayPersonaggi = dataApi
    })
  }
}

}
</script>

<template>
  <NavComp/>
<div class="sfondo">
  <div class="box d-flex align-items-center flex-column my-5 ">
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
