<template>
  <div id="app">
    <header>
      <div class="heading mb-5">
        <img src="https://www.freepnglogos.com/uploads/spotify-logo-png/file-spotify-logo-png-4.png" alt="Spotify logo">
      </div>
      
    </header>
    <div v-if="booleano == true" class="container">
        <div class="row justify-content-center">
            <div v-for="(element, index) in dischiGroup" :key="index" class=" col-lg-2 col-md-4 col-6 dischi-container mb-3 mx-3">
            <Dischi :disco='element'/> 
            </div>
        </div>
    </div>
    <div v-else class="loading">
      <h2 class="text-white">Caricamento..</h2>
      <div class="progress caricamento">
        <div class="progress-bar progress-bar-striped progress-bar-animated" role="progressbar" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100" style="width: 75%"></div>
      </div>
    </div>
      
      
  </div>
</template>

<script>

import Dischi from './components/Dischi.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Dischi,
  },
  data: function(){
    return{
      dischiGroup: [],
      booleano: false
    }
  },
  created: function(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(response =>{
      this.dischiGroup = response.data.response.slice();
      setTimeout(()=>{
        this.booleano = true;
      } , 1500)
      
    })
  }
}
</script>

<style lang="scss">
@import 'style/general.scss';
.heading{
  height: 100px;
  background-color: #2e3a46;
  line-height: 100px;
  padding-left: 20px;
  img{
  width: 60px;
}
}
.dischi-container{
   
    background-color: #2e3a46;
    color: white;
   
}
.caricamento{
  width: 100%;
}
.loading{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
