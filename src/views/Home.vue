<template>
  <div class="home">
    <input type="text" placeholder="Pokemon zoeken" class="border-2 p-2 text-center rounded-xl m-3" v-model="filterPokemon">
    <div v-for="pokemon in filteredItems" :key="pokemon.id" class="flex p-3 border-2 m-3 rounded-xl justify-around">
     <div class="flex-col">
        <h2 class="">{{pokemon.name}}</h2>
        <p class="">Nr. {{pokemon.id}}</p>
      </div> 
          <p class="m-3 text-right">{{pokemon.types[0].type.name}}</p>
          <p class="m-3 text-right" v-if="pokemon.types.length > 1">{{pokemon.types[1].type.name}}</p>
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
      filterPokemon: ''
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
