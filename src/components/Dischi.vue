<template>
  <div class="text-center">
      <img class="img-fluid" :src="disco.poster" :alt="disco.author">
      <h2 class="mt-2">{{disco.title}}</h2>
      <div class="p-3">
          <h3>{{disco.author}}</h3>
            <h4>{{disco.year}}</h4>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Dischi',
    props:['disco']
}
</script>

<style scoped lang='scss'>
 img{
        width: 100%;
        object-fit: cover;
        object-position: center;
        
        padding: 10px;
        padding-top: 15px;
    }
    h3,
    h4{
        color: grey;
    }

</style>