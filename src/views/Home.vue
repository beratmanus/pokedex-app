<template>
  <div class="home">
    <input type="text" placeholder="Pokemon zoeken" class="border-2 p-2 text-center rounded-xl m-3" v-model="filterPokemon">
    
    <div v-for="pokemon in filteredItems" :key="pokemon.id" class="flex p-2 m-3 border-2 rounded-xl justify-between capitalize">
      <div class="flex">
        <img :src=pokemon.sprites.front_default alt="" class="">
      <div class="flex-col m-2">
          <h2 class="text-left">{{pokemon.name}}</h2>
          <p class="text-left">Nr. {{pokemon.id}}</p>
        </div> 
      </div>
      <div class="flex">
          <p class="text-right border-2 m-1 rounded-xl h-8 py-1 px-3">{{pokemon.types[0].type.name}}</p>
          <p class="text-center border-2 m-1 rounded-xl h-8 py-1 px-3" v-if="pokemon.types.length > 1">{{pokemon.types[1].type.name}}</p>
          <p class="m-2">></p>
        </div>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
//details api: https://pokeapi.co/api/v2/pokemon/133  

const listPokemonUrl = "https://stoplight.io/mocks/appwise-be/pokemon/57519009/pokemon"

export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      pokemons: [],
      filterPokemon: '',
    }
  },
  mounted() {
    fetch(listPokemonUrl)
    .then(res => res.json())
    .then(data => this.pokemons = data)
  },
   computed: {
    filteredItems() {
      return this.pokemons.filter((pokemon) => {
        return pokemon.name.toLowerCase().includes(this.filterPokemon.toLowerCase());
      });
    },
    },
  }

</script>
<style>
  img{
    height: 70px;
    width: 70px;
  }

  p{
    font-size: 12px;
  }
</style>
