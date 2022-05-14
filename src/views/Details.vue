<template>
<div>
  <button @click="goBack" class="flex p-2"> <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
  <path stroke-linecap="round" stroke-linejoin="round" d="M10 19l-7-7m0 0l7-7m-7 7h18" />
</svg> <span class="px-2">Terug</span></button>
  <h1 class="text-left p-4 text-4xl capitalize font-bold">{{name}}</h1>
  <img :src=img alt="" >
  <PokemonInfo />
  <PokemonStats />
  <PokemonMoveset />
  
</div>
</template>

<script>
import PokemonInfo from "../components/PokemonInfo.vue"
import PokemonStats from "../components/PokemonStats.vue"
import PokemonMoveset from "../components/PokemonMoveset.vue"
export default {
  props: ['id' , 'name' , 'img'],
  components: {
    PokemonInfo,
    PokemonStats,
    PokemonMoveset
  },
  methods: {
    goBack() {
      return this.$router.go(-1);
    }
  }
}
</script>
<style scoped>
img{
  width: 200px;
  height: 200px;
}



</style>