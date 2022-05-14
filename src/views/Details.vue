<template>
<div>
  <h1 class="text-left p-4 text-4xl capitalize font-bold">{{name}}</h1>
  <img :src=img alt="" class="w-full">
  <p>{{pokemonData}}</p>
  
</div>
</template>

<script>
export default {
  props: ['id' , 'name' , 'img'],
  data() {
    return {
      pokemonData: '',
      imgUrl: ''
    }
  },
  mounted() {
    fetch('https://pokeapi.co/api/v2/pokemon/' + this.$route.params.id)
    .then(res => res.json())
    .then(data => this.pokemonData = data)
  },
  computed(){
    
  }
  
}
</script>
<style>
  img{
    
  }

</style>