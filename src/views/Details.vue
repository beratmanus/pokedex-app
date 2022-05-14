<template>
<div :id="type">
  <button @click="goBack" class="flex p-2"> <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
  <path stroke-linecap="round" stroke-linejoin="round" d="M10 19l-7-7m0 0l7-7m-7 7h18" />
</svg> <span class="px-2">Terug</span></button>
  <h1 class="text-left p-4 text-4xl text-white capitalize font-bold">{{name}}</h1>
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
  props: ['id' , 'name' , 'img','type'],
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
#grass {
    background-color: #95C24D;
}
#poison {
    background-color: #BA7EC8;
}
#fire {
    background-color: #FD7D25;
}
#water {
    background-color: #4592C3;
}
#electric {
    background-color: #FFCF00;
}
#ground {
    background-color: #D5B35B;
}
#fighting {
    background-color: #A23B6C;
}
#psychic {
    background-color: #F85888;
}
#rock {
    background-color: #B6A136;
}
#ice {
    background-color: #36e1ff;
}
#ghost {
    background-color: #7B62A3;
}
#normal {
    background-color: #A3ACAE;
}
#flying {
    background-color: #6ab2de;
}
#bug {
    background-color: #6d9036;
}
#fairy {
    background-color: #F8D4F3;
}
#dragon {
    background-color: #8B4513;
}
#steel {
    background-color: #303030;
}


</style>