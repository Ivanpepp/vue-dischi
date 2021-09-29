<template>
  <div id="app">
    <div class="container">
        <div class="row justify-content-center">
            <div v-for="(element, index) in dischiGroup" :key="index" class="col-lg-3 col-md-4 col-6 dischi-container mb-3 mx-3">
            <Dischi :disco='element'/> 
            </div>
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
    }
  },
  created: function(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(response =>{
      this.dischiGroup = response.data.response.slice();
    })
  }
}
</script>

<style lang="scss">
@import 'style/general.scss';
.dischi-container{
    height: 500px;
    width: 300px;
    background-color: #2e3a46;
    color: white;
   
}
</style>
